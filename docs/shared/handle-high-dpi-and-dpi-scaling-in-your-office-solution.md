---
title: "Handle high DPI and DPI scaling in your Office solution"
description: "Update your Office solution such as custom task panes, or ActiveX controls, to support high DPI monitors."  
ms.date: 12/18/2018
localization_priority: Normal
---

# Handle high DPI and DPI scaling in your Office solution

Many computer and display configurations now support high DPI (dots-per-inch) resolutions, and can connect multiple monitors with different sizes and pixel densities. This requires applications to adjust when the user moves the app to a monitor with a different DPI, or changes the zoom level. Applications that don’t support DPI scaling might look fine on low DPI monitors, but will look stretched and blurry when shown on a high DPI monitor. 

Office 2016 applications, such as Word and Excel, have been updated to respond to changes in scale factor. However, your Office solution must also respond to changes to draw correctly when the DPI changes. This article describes how Office supports dynamic DPI, and what steps you can take to ensure the best viewing experience for your Office extensibility solution to handle DPI scaling. 

## DPI scaling symptoms in your solution

Windows applies DPI scaling when an application is moved from one display to another display with a different DPI. This happens in scenarios such as dragging an application to a different monitor or docking your laptop. If your Office solution is adversely affected by DPI scaling, you will see one or more of the following symptoms:

- The windows draw in the wrong location or have incorrect sizing.
- Elements such as buttons and labels appear in the wrong location in your solution’s window.
- Fonts and images appear too small, too large or in the wrong location.

The following types of Office solutions can be affected by DPI scaling:

- VSTO Add-ins
- Custom task panes
- COM Add-ins
- ActiveX controls
- Ribbon extensions
- Ole servers
- Office web add-ins

## Windows DPI awareness modes

Throughout this article we’ll refer to the DPI awareness modes that Windows supports. Each DPI awareness mode supports different capabilities, as described in the following table. This is a simplified description of the modes to explain how Office solutions support them. For more information about the DPI awareness modes, see [High DPI Desktop Application Development on Windows](https://docs.microsoft.com/en-us/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).

|Mode  |Description  |When DPI changes  |
|---------|---------|---------|
|DPI unaware     |    Application always renders as if it is on a display with a DPI value of 96.     |    Application is bitmap stretched to expected size on primary and secondary displays.    |
|System DPI aware     |   Application detects the DPI of the primary connected monitor at Windows login but cannot respond to DPI changes. For more information, see Configure Windows to fix blurry apps section in this article.      |     Application is bitmap stretched when moved to a new display with a different DPI.    |
|Per Monitor DPI aware     |    Application is capable of redrawing itself correctly when the DPI changes.     |    Windows will send DPI notifications to top-level windows in the application so that it can redraw when the DPI changes.     |
|Per Monitor v2     |   Application is capable of redrawing itself correctly when the DPI changes.      |        Windows will send DPI notifications to both top-level and child windows so that the application can redraw when the DPI changes. |

## How Office supports DPI scaling

The most significant factor in determining how your Office solution can handle DPI scaling is whether your solution is a top-level window, or a child window. The following picture shows a few examples of Office solutions running as top-level or child windows, and which DPI awareness mode they will use on Windows April 2018 Update (1803) and later.

![Excel hosting an ActiveX control and custom task pane as child windows. A separate VSTO/COM add-in runs as a top-level window. Office is a top-level window.](./media/office-dpi-awareness-for-solution-types.png)

In this image:
- The COM/VSTO top-level window is Per Monitor DPI aware.
- The ActiveX control child window is System DPI aware.
- The Office top-level window is Per Monitor DPI aware.
- The custom task pane child window is System DPI aware.

## Managing thread DPI context

When the host Office app starts, its main thread runs in Per Monitor DPI aware context. When your solution code creates threads, or receives calls from Office, you need to manage the thread DPI context.

### Creating new threads with the correct DPI context

If your solution creates additional threads, Office will force the threads into Per Monitor DPI aware context. If your code expects a different context, you need to use the SetThreadDpiAwarenessContext function to set the expected thread DPI awareness. 

### Build a context block for incoming thread calls

![Diagram showing context block in Office app switching the thread to System Aware context on calls to your top-level window.](./media/thread-dpi-awareness-context-block.png)

Your solution will interact with its host Office app, so you will have incoming calls to your solution from Office such as event callbacks. When Office calls your solution, it has a context block that forces the thread context to be in System DPI Aware context. You must change the thread context to match the DPI awareness of your window. You can implement a similar context block to switch the thread context on incoming calls. Use the SetThreadDpiAwarenessContext function to change the context to match your window context. 

> [!NOTE]
> Your context block should restore the original DPI thread context before calling other components outside of your solution code.

#### Managed code context block

The following example code shows how to construct your own context block.

``` c#
public struct DPI_AWARENESS_CONTEXT
        {
            private IntPtr value;

            private DPI_AWARENESS_CONTEXT(IntPtr value)
            {
                this.value = value;
            }
            public static implicit operator DPI_AWARENESS_CONTEXT(IntPtr value)
            {
                return new DPI_AWARENESS_CONTEXT(value);
            }

            public static implicit operator IntPtr(DPI_AWARENESS_CONTEXT context)
            {
                return context.value;
            }

            public static DPI_AWARENESS_CONTEXT operator -(DPI_AWARENESS_CONTEXT context, long value)
            {
                return (IntPtr)(context.value.ToInt64() - value);
            }
            public static DPI_AWARENESS_CONTEXT operator -(DPI_AWARENESS_CONTEXT context, int value)
            {
                return (IntPtr)(context.value.ToInt32() - value);
            }

            public static bool operator ==(DPI_AWARENESS_CONTEXT context1, DPI_AWARENESS_CONTEXT context2)
            {
                return context1.value == context2;
            }
            public static bool operator !=(DPI_AWARENESS_CONTEXT context1, DPI_AWARENESS_CONTEXT context2)
            {
                return context1.value != context2;
            }

            public static bool operator ==(IntPtr context1, DPI_AWARENESS_CONTEXT context2)
            {
                return AreDpiAwarenessContextsEqual(context1, context2);
            }
            public static bool operator !=(IntPtr context1, DPI_AWARENESS_CONTEXT context2)
            {
                return !AreDpiAwarenessContextsEqual(context1, context2);
            }

            public override bool Equals(object obj)
            {
                return base.Equals(obj);
            }

            public override int GetHashCode()
            {
                return base.GetHashCode();
            }

            public override string ToString()
            {
                if (this.value == DPI_AWARENESS_CONTEXT_UNAWARE)
                {
                    return "Unaware";
                }
                if (this.value == DPI_AWARENESS_CONTEXT_SYSTEM_AWARE)
                {
                    return "System Aware";
                }
                if (this.value == DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE)
                {
                    return "Per Monitor Aware";
                }
                if (this.value == DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2)
                {
                    return "Per Monitor Aware V2";
                }
                return "Unknown";
            }
        }

        private static DPI_AWARENESS_CONTEXT DPI_AWARENESS_CONTEXT_HANDLE = IntPtr.Zero;

        public static readonly DPI_AWARENESS_CONTEXT DPI_AWARENESS_CONTEXT_INVALID = IntPtr.Zero;
        public static readonly DPI_AWARENESS_CONTEXT DPI_AWARENESS_CONTEXT_UNAWARE = DPI_AWARENESS_CONTEXT_HANDLE - 1;
        public static readonly DPI_AWARENESS_CONTEXT DPI_AWARENESS_CONTEXT_SYSTEM_AWARE = DPI_AWARENESS_CONTEXT_HANDLE - 2;
        public static readonly DPI_AWARENESS_CONTEXT DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE = DPI_AWARENESS_CONTEXT_HANDLE - 3;
        public static readonly DPI_AWARENESS_CONTEXT DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2 = DPI_AWARENESS_CONTEXT_HANDLE - 4;

        public static DPI_AWARENESS_CONTEXT[] DpiAwarenessContexts =
        {
            DPI_AWARENESS_CONTEXT_UNAWARE,
            DPI_AWARENESS_CONTEXT_SYSTEM_AWARE,
            DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE,
            DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE_V2
        };

class DPIContextBlock : IDisposable
    {
        private DPI_AWARENESS_CONTEXT resetContext;
        private bool disposed = false;

        public DPIContextBlock(DPI_AWARENESS_CONTEXT contextSwitchTo)
        {
            resetContext = SetThreadDpiAwarenessContext(contextSwitchTo);
         }

        public void Dispose()
        {
            Dispose(true);
            GC.SuppressFinalize(this);
        }

        protected virtual void Dispose(bool disposing)
        {
            if (!disposed)
            {
                if (disposing)
                {
                    SetThreadDpiAwarenessContext(resetContext);
                }
            }
            disposed = true;
        }
    }
```

#### Native code context block

``` c++
#include <winuser.h>
/* DpiAwarenessContextBlock can be used to simplify setting and resetting the DPI_AWARENESS_CONTEXT of
the current thread.  When the object is constructed, the DPI_AWARENESS_CONTEXT is set, and when the object is
destructed, the DPI awareness context is reverted to the previous awareness context at construct time.

This object allows us to write code such as:

// Thread state is currently DPI_AWARENESS_SYSTEM_AWARE
if (condition)
{
DpiAwarenessContextBlock perMonitorAware(DPI_AWARENESS_PER_MONITOR_AWARE);
... // Create a top-level hwnd with the current thread state, DPI_AWARENESS_PER_MONITOR_AWARE
}
// Thread state automatically returns to DPI_AWARENESS_SYSTEM_AWARE

*/
class DpiAwarenessContextBlock
{
public:
      DpiAwarenessContextBlock(DPI_AWARENESS_CONTEXT dpiContext) noexcept;
      ~DpiAwarenessContextBlock();

      // Copy and move are not to be used with these context objects
      DpiAwarenessContextBlock(const DpiAwarenessContextBlock&) = delete;
      DpiAwarenessContextBlock(DpiAwarenessContextBlock&&) = delete;

private:
      DPI_AWARENESS_CONTEXT m_contextReversalType;
      bool m_doContextSwitch;
};

inline DpiAwarenessContextBlock::DpiAwarenessContextBlock(DPI_AWARENESS_CONTEXT dpiContext) noexcept
{
      m_contextReversalType = SetThreadDpiAwarenessContext(dpiContext);
}

inline DpiAwarenessContextBlock::~DpiAwarenessContextBlock()
{
      SetThreadDpiAwarenessContext(m_contextReversalType);
}
```

## Top-level window management

When Office applications start, a call is made to SetThreadDpiAwarenessContext as DPI_AWARENESS_CONTEXT_PER_MONITOR_AWARE. In this context, DPI changes are sent to the HWND of any top-level windows in the process that are running as Per Monitor DPI aware. Top-level windows are the Office application window, and any additional top-level windows created by your solution. When an Office application is moved to a new display, it gets notified so that it can dynamically scale and draw correctly in the DPI of the new display. Your Office solution can create top-level windows that are in any DPI awareness mode. Your top-level windows can also respond to DPI changes by listening to Windows messages for the changes.

If you create child windows that are parented to your top-level window, you can also set them to any DPI awareness mode. However, if you use Per Monitor DPI aware mode, your child windows will not receive DPI change notifications.  For more information about Windows DPI awareness modes, see High DPI Desktop Application Development on Windows.

## Child window management

When working with ActiveX controls and custom task panes, Office creates the child window for your solution. You can create additional child windows, but you have to be aware of the parent window DPI awareness. Office runs in Per Monitor DPI awareness mode, which means any child windows in your solution will not get DPI change notifications. Only Per Monitor v2 mode supports sending DPI changes to child windows (Office does not support Per Monitor v2). However, for ActiveX controls, there is a workaround. For more information, see the ActiveX controls section later in this article.

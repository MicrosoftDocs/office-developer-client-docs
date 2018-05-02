---
title: "About Currency Constants"
 
 
manager: soliver
ms.date: 3/9/2015
ms.audience: Developer
ms.topic: overview
f1_keywords:
- Vis_DSS.chm82253123
 
localization_priority: Normal
ms.assetid: d94c740f-29e1-1e7f-39f6-8aa215f3111d
description: "To format a number as currency, you can use the CY function and pass an optional constant to specify which country/region's currency to use. The currency constants can be specified as the ID number that corresponds to a country/region or as a string (enclosed in quotation marks) that corresponds to an ISO 4217 three-character abbreviation."
---

# About Currency Constants

To format a number as currency, you can use the CY function and pass an optional constant to specify which country/region's currency to use. The currency constants can be specified as the ID number that corresponds to a country/region or as a string (enclosed in quotation marks) that corresponds to an ISO 4217 three-character abbreviation.
  
If you show currency symbols for nonlocal currencies, and the system does not know the symbol for a given currency, the dollar symbol ($) is displayed.
  
## IDs and abbreviations

|**ID**|**Abbreviation**|**Currency**|
|:-----|:-----|:-----|
| 0  <br/> | SYS  <br/> | Uses system settings  <br/> |
| 1  <br/> | XXX  <br/> | Formats as a number  <br/> |
| 2 - 9  <br/> | Reserved  <br/> |
| 10  <br/> | EUR  <br/> | Euro  <br/> |
| 11  <br/> | USD  <br/> | U.S. dollar  <br/> |
| 12  <br/> | ATS  <br/> | Austrian Schilling  <br/> |
| 13  <br/> | AUD  <br/> | Australian Dollar  <br/> |
| 14  <br/> | BEF  <br/> | Belgian Franc  <br/> |
| 15  <br/> | CAD  <br/> | Canadian Dollar  <br/> |
| 16  <br/> | CHF  <br/> | Swiss Franc  <br/> |
| 17  <br/> | CNY  <br/> | Chinese Yuan Renminbi  <br/> |
| 18  <br/> | DEM  <br/> | German Mark  <br/> |
| 19  <br/> | DKK  <br/> | Danish Krone  <br/> |
| 20  <br/> | ESP  <br/> | Spanish Peseta  <br/> |
| 21  <br/> | FIM  <br/> | Finnish Markka  <br/> |
| 22  <br/> | FRF  <br/> | French Franc  <br/> |
| 23  <br/> | GBP  <br/> | British Pound Sterling  <br/> |
| 24  <br/> | GRD  <br/> | Greek Drachma  <br/> |
| 25  <br/> | HKD  <br/> | Hong Kong Special Administrative Region (SAR) Dollar  <br/> |
| 26  <br/> | HUF  <br/> | Hungarian Forint  <br/> |
| 27  <br/> | IDR  <br/> | Indonesian Rupiah  <br/> |
| 28  <br/> | IEP  <br/> | Irish Punt  <br/> |
| 29  <br/> | ILS  <br/> | Israeli Shekel  <br/> |
| 30  <br/> | ITL  <br/> | Italian Lira  <br/> |
| 31  <br/> | JPY  <br/> | Japanese Yen  <br/> |
| 32  <br/> | KRW  <br/> | Korean Won  <br/> |
| 33  <br/> | LUF  <br/> | Luxembourgian Franc  <br/> |
| 34  <br/> | MXN  <br/> | Mexican Peso  <br/> |
| 35  <br/> | MYR  <br/> | Malaysian Ringgit  <br/> |
| 36  <br/> | NLG  <br/> | Dutch Guilder  <br/> |
| 37  <br/> | NOK  <br/> | Norwegian Krone  <br/> |
| 38  <br/> | NZD  <br/> | New Zealand Dollar  <br/> |
| 39  <br/> | PHP  <br/> | Philippine Peso  <br/> |
| 40  <br/> | PLZ (Historic. Use PLN.)  <br/> | Polish Zloty  <br/> |
| 41  <br/> | PTE  <br/> | Portuguese Escudo  <br/> |
| 42  <br/> | ROL  <br/> | Romanian Leu  <br/> |
| 43  <br/> | RUR (Historic. Use RUB.)  <br/> | Russian Ruble  <br/> |
| 44  <br/> | SEK  <br/> | Swedish Kroner  <br/> |
| 45  <br/> | SGD  <br/> | Singapore Dollar  <br/> |
| 46  <br/> | THB  <br/> | Thai Baht  <br/> |
| 47  <br/> | TWD  <br/> | New Taiwan Dollar  <br/> |
| 48  <br/> | XEU (Historic. Use EUR.)  <br/> | ECU (pre-1998)  <br/> |
| 49  <br/> | YUN (Historic. Use YUM.)  <br/> | Yugoslavian Dinar  <br/> |
| 50  <br/> | ZAR  <br/> | South African Rand  <br/> |
| 51 - 55  <br/> | Reserved  <br/> |
| 56  <br/> | ARS  <br/> | Argentinean Peso  <br/> |
| 57  <br/> | BMD  <br/> | Bermudian Dollar  <br/> |
| 58  <br/> | BOB  <br/> | Bolivian Boliviano  <br/> |
| 59  <br/> | BRR (Historic. Use BRL.)  <br/> | Brazilian Cruziero Real  <br/> |
| 60  <br/> | BSD  <br/> | Bahamanian Dollar  <br/> |
| 61  <br/> | CLP  <br/> | Chilean Peso  <br/> |
| 62  <br/> | COP  <br/> | Colombian Peso  <br/> |
| 63  <br/> | CRC  <br/> | Costa Rican Colon  <br/> |
| 64  <br/> | CZK  <br/> | Czech Koruna  <br/> |
| 65  <br/> | DOP  <br/> | Dominican Peso  <br/> |
| 66  <br/> | ECS  <br/> | Ecuadorean Sucre  <br/> |
| 67  <br/> | EGP  <br/> | Egyptian Pound  <br/> |
| 68  <br/> | HNL  <br/> | Honduran Lempira  <br/> |
| 69  <br/> | INR  <br/> | Indian Rupee  <br/> |
| 70  <br/> | JMD  <br/> | Jamaican Dollar  <br/> |
| 71  <br/> | JOD  <br/> | Jordanian Dinar  <br/> |
| 72  <br/> | KWD  <br/> | Kuwaiti Dinar  <br/> |
| 73  <br/> | MOP  <br/> | Macanese Pataca  <br/> |
| 74  <br/> | NIO  <br/> | Nicaraguan Cordoba Oro  <br/> |
| 75  <br/> | PAB  <br/> | Panamanian Balboa  <br/> |
| 76  <br/> | PEN  <br/> | Peruvian Nuevo Sol  <br/> |
| 77  <br/> | PKR  <br/> | Pakistani Rupee  <br/> |
| 78  <br/> | PYG  <br/> | Paraguayan Guarani  <br/> |
| 79  <br/> | SAR  <br/> | Saudi Riyal  <br/> |
| 80  <br/> | SIT  <br/> | Slovenian Tolar  <br/> |
| 81  <br/> | SKK  <br/> | Slovakian Koruna  <br/> |
| 82  <br/> | SVC  <br/> | El Salvadoran Colon  <br/> |
| 83  <br/> | TRY  <br/> | New Turkish Lira  <br/> |
| 84  <br/> | TTD  <br/> | Trinidad and Tobago Dollar  <br/> |
| 85  <br/> | UYU  <br/> | Uruguayan Peso Uruguayo  <br/> |
| 86  <br/> | VEB  <br/> | Venezuelan Bolivar  <br/> |
| 87  <br/> | VND  <br/> | Vietnamese Dong  <br/> |
| 88  <br/> | BRL  <br/> | Brazilian Real  <br/> |
| 89  <br/> | PLN  <br/> | Polish Zloty  <br/> |
| 90  <br/> | RUB  <br/> | Russian Ruble  <br/> |
| 91  <br/> | YUM  <br/> | Yugoslavian Dinar  <br/> |
| 92  <br/> | BYB (Historic. Use BYR.)  <br/> | Belarusian Ruble  <br/> |
| 93  <br/> | UAH  <br/> | Ukrainian Hryvnia  <br/> |
| 94  <br/> | AFA  <br/> | Afghani (added in Visio 2002)  <br/> |
| 95  <br/> | ALL  <br/> | Lek (added in Visio 2002)  <br/> |
| 96  <br/> | DZD  <br/> | Algerian Dinar (added in Visio 2002)  <br/> |
| 97  <br/> | ADP  <br/> | Andorran Peseta (added in Visio 2002)  <br/> |
| 98  <br/> | AOA  <br/> | Kwanza (added in Visio 2002)  <br/> |
| 99  <br/> | XCD  <br/> | East Caribbean Dollar (added in Visio 2002)  <br/> |
| 100  <br/> | AMD  <br/> | Armenian Dram (added in Visio 2002)  <br/> |
| 101  <br/> | AWG  <br/> | Aruban Guilder (added in Visio 2002)  <br/> |
| 102  <br/> | AZM  <br/> | Azerbaijanian Manat (added in Visio 2002)  <br/> |
| 103  <br/> | BHD  <br/> | Bahraini Dinar (added in Visio 2002)  <br/> |
| 104  <br/> | BDT  <br/> | Taka (added in Visio 2002)  <br/> |
| 105  <br/> | BBD  <br/> | Barbados Dollar (added in Visio 2002)  <br/> |
| 106  <br/> | BYR  <br/> | Belarussian Ruble (added in Visio 2002)  <br/> |
| 107  <br/> | BZD  <br/> | Belize Dollar (added in Visio 2002)  <br/> |
| 108  <br/> | XOF  <br/> | CFA Franc BCEAO (added in Visio 2002)  <br/> |
| 109  <br/> | BTN  <br/> | Ngultrum (added in Visio 2002)  <br/> |
| 110  <br/> | BAM  <br/> | Convertible Marks (added in Visio 2002)  <br/> |
| 111  <br/> | BWP  <br/> | Pula (added in Visio 2002)  <br/> |
| 112  <br/> | BND  <br/> | Brunei Dollar (added in Visio 2002)  <br/> |
| 113  <br/> | BGL (Historic. Use BGN.)  <br/> | Lev  <br/> |
| 114  <br/> | BGN  <br/> | Bulgarian Lev (added in Visio 2002)  <br/> |
| 115  <br/> | BIF  <br/> | Burundi Franc (added in Visio 2002)  <br/> |
| 116  <br/> | KHR  <br/> | Riel (added in Visio 2002)  <br/> |
| 117  <br/> | XAF  <br/> | CFA Franc BEAC (added in Visio 2002)  <br/> |
| 118  <br/> | CVE  <br/> | Cape Verde Escudo (added in Visio 2002)  <br/> |
| 119  <br/> | KYD  <br/> | Cayman Islands Dollar (added in Visio 2002)  <br/> |
| 120  <br/> | KMF  <br/> | Comoro Franc (added in Visio 2002)  <br/> |
| 121  <br/> | CDF  <br/> | Franc Congolais (added in Visio 2002)  <br/> |
| 122  <br/> | HRK  <br/> | Croatian Kuna (added in Visio 2002)  <br/> |
| 123  <br/> | CUP  <br/> | Cuban Peso (added in Visio 2002)  <br/> |
| 124  <br/> | CYP  <br/> | Cyprus Pound (added in Visio 2002)  <br/> |
| 125  <br/> | DJF  <br/> | Djibouti Franc (added in Visio 2002)  <br/> |
| 126  <br/> | TPE  <br/> | Timor Escudo (added in Visio 2002)  <br/> |
| 127  <br/> | ERN  <br/> | Nakfa (added in Visio 2002)  <br/> |
| 128  <br/> | EEK  <br/> | Kroon (added in Visio 2002)  <br/> |
| 129  <br/> | ETB  <br/> | Ethiopian Birr (added in Visio 2002)  <br/> |
| 130  <br/> | FKP  <br/> | Falkland Islands (Islas Malvinas) Pound (added in Visio 2002)  <br/> |
| 131  <br/> | FJD  <br/> | Fijian Dollar (added in Visio 2002)  <br/> |
| 132  <br/> | XPF  <br/> | CFP Franc (added in Visio 2002)  <br/> |
| 133  <br/> | GMD  <br/> | Dalasi (added in Visio 2002)  <br/> |
| 134  <br/> | GEL  <br/> | Lari (added in Visio 2002)  <br/> |
| 135  <br/> | GHC  <br/> | Cedi (added in Visio 2002)  <br/> |
| 136  <br/> | GIP  <br/> | Gibraltar Pound (added in Visio 2002)  <br/> |
| 137  <br/> | GTQ  <br/> | Quetzal (added in Visio 2002)  <br/> |
| 138  <br/> | GNF  <br/> | Guinea Franc (added in Visio 2002)  <br/> |
| 139  <br/> | GWP  <br/> | Guinea-Bissau Peso (added in Visio 2002)  <br/> |
| 140  <br/> | GYD  <br/> | Guyana Dollar (added in Visio 2002)  <br/> |
| 141  <br/> | HTG  <br/> | Gourde (added in Visio 2002)  <br/> |
| 142  <br/> | ISK  <br/> | Iceland Krona (added in Visio 2002)  <br/> |
| 143  <br/> | IRR  <br/> | Iranian Rial (added in Visio 2002)  <br/> |
| 144  <br/> | IQD  <br/> | Iraqi Dinar (added in Visio 2002)  <br/> |
| 145  <br/> | KZT  <br/> | Tenge (added in Visio 2002)  <br/> |
| 146  <br/> | KES  <br/> | Kenyan Shilling (added in Visio 2002)  <br/> |
| 147  <br/> | KPW  <br/> | North Korean Won (added in Visio 2002)  <br/> |
| 148  <br/> | KGS  <br/> | Som (added in Visio 2002)  <br/> |
| 149  <br/> | LAK  <br/> | Kip (added in Visio 2002)  <br/> |
| 150  <br/> | LVL (Historic. Use EUR.)  <br/> | Latvian Lats (added in Visio 2002)  <br/> |
| 151  <br/> | LBP  <br/> | Lebanese Pound (added in Visio 2002)  <br/> |
| 152  <br/> | LSL  <br/> | Loti (added in Visio 2002)  <br/> |
| 153  <br/> | LRD  <br/> | Liberian Dollar (added in Visio 2002)  <br/> |
| 154  <br/> | LYD  <br/> | Libyan Dinar (added in Visio 2002)  <br/> |
| 155  <br/> | LTL  <br/> | Lithuanian Litus (added in Visio 2002)  <br/> |
| 156  <br/> | MKD  <br/> | Denar (added in Visio 2002)  <br/> |
| 157  <br/> | MGF (Historic. Use MGA.)  <br/> | Madagascar Franc (added in Visio 2002)  <br/> |
| 158  <br/> | MWK  <br/> | Malawian Kwacha (added in Visio 2002)  <br/> |
| 159  <br/> | MVR  <br/> | Rufiyaa (added in Visio 2002)  <br/> |
| 160  <br/> | MTL  <br/> | Maltese Lira (added in Visio 2002)  <br/> |
| 161  <br/> | MRO  <br/> | Ouguiya (added in Visio 2002)  <br/> |
| 162  <br/> | MUR  <br/> | Mauritius Rupee (added in Visio 2002)  <br/> |
| 163  <br/> | MDL  <br/> | Moldovan Leu (added in Visio 2002)  <br/> |
| 164  <br/> | MNT  <br/> | Tugrik (added in Visio 2002)  <br/> |
| 165  <br/> | MAD  <br/> | Moroccan Dirham (added in Visio 2002)  <br/> |
| 166  <br/> | MZM  <br/> | Metical (added in Visio 2002)  <br/> |
| 167  <br/> | MMK  <br/> | Kyat (added in Visio 2002)  <br/> |
| 168  <br/> | NAD  <br/> | Namibia Dollar (added in Visio 2002)  <br/> |
| 169  <br/> | NPR  <br/> | Nepalese Rupee (added in Visio 2002)  <br/> |
| 170  <br/> | ANG  <br/> | Netherlands Antillian Guilder (added in Visio 2002)  <br/> |
| 171  <br/> | NGN  <br/> | Naira (added in Visio 2002)  <br/> |
| 172  <br/> | OMR  <br/> | Rial Omani (added in Visio 2002)  <br/> |
| 173  <br/> | PGK  <br/> | Kina (added in Visio 2002)  <br/> |
| 174  <br/> | QAR  <br/> | Qatari Rial (added in Visio 2002)  <br/> |
| 175  <br/> | RWF  <br/> | Rwanda Franc (added in Visio 2002)  <br/> |
| 176  <br/> | SHP  <br/> | Saint Helena Pound (added in Visio 2002)  <br/> |
| 177  <br/> | WST  <br/> | Tala (added in Visio 2002)  <br/> |
| 178  <br/> | STD  <br/> | Dobra (added in Visio 2002)  <br/> |
| 179  <br/> | SCR  <br/> | Seychelles Rupee (added in Visio 2002)  <br/> |
| 180  <br/> | SLL  <br/> | Leone (added in Visio 2002)  <br/> |
| 181  <br/> | SBD  <br/> | Solomon Islands Dollar (added in Visio 2002)  <br/> |
| 182  <br/> | SOS  <br/> | Somali Shilling (added in Visio 2002)  <br/> |
| 183  <br/> | LKR  <br/> | Sri Lanka Rupee (added in Visio 2002)  <br/> |
| 184  <br/> | SDD  <br/> | Sudanese Dinar (added in Visio 2002)  <br/> |
| 185  <br/> | SRG  <br/> | Suriname Guilder (added in Visio 2002)  <br/> |
| 186  <br/> | SZL  <br/> | Lilangeni (added in Visio 2002)  <br/> |
| 187  <br/> | SYP  <br/> | Syrian Pound (added in Visio 2002)  <br/> |
| 188  <br/> | TJR (Historic. Use TJS.)  <br/> | Tajik Ruble  <br/> |
| 189  <br/> | TJS  <br/> | Tajik Somoni (added in Visio 2002)  <br/> |
| 190  <br/> | TZS  <br/> | Tanzanian Shilling (added in Visio 2002)  <br/> |
| 191  <br/> | TOP  <br/> | Pa'anga (added in Visio 2002)  <br/> |
| 192  <br/> | TND  <br/> | Tunisian Dinar (added in Visio 2002)  <br/> |
| 193  <br/> | TMM  <br/> | Manat (added in Visio 2002)  <br/> |
| 194  <br/> | UGX  <br/> | Uganda Shilling (added in Visio 2002)  <br/> |
| 195  <br/> | AED  <br/> | UAE Dirham (added in Visio 2002)  <br/> |
| 196  <br/> | UZS  <br/> | Uzbekistan Sum (added in Visio 2002)  <br/> |
| 197  <br/> | VUV  <br/> | Vatu (added in Visio 2002)  <br/> |
| 198  <br/> | YER  <br/> | Yemeni Rial (added in Visio 2002)  <br/> |
| 199  <br/> | ZMK  <br/> | Zambian Kwacha (added in Visio 2002)  <br/> |
| 200  <br/> | ZWD  <br/> | Zimbabwe Dollar (added in Visio 2002)  <br/> |
|201  <br/> |VEF  <br/> |Venezuelan Bolivar Fuente (added in Visio 2010)  <br/> |
|202  <br/> |MGA  <br/> |Malagasy Ariary (added in Visio 2010)  <br/> |
|203  <br/> |RSD  <br/> |Serbian Dinar (added in Visio 2010)  <br/> |
|204  <br/> |CSD (Historic. Use RSD.)  <br/> |Serbian Dinar (added in Visio 2010)  <br/> |
   


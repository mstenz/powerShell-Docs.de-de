---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Entfernen der Konfigurationsdateien.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_removeconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Entfernt die Konfigurationsdateien.

Syntax
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

Parameter
----------

*Stage* \[in\]  
Gibt an, welches Konfigurationsdokument entfernt werden soll. Die folgenden Werte sind gültig:

|Wert |Beschreibung |
|:--- |:---|
|**1** | Das **aktuelle** (Current) Konfigurationsdokument (current.mof). |
|**2** | Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).  |
|**4** | Das **vorherige** (Previous) Konfigurationsdokument (previous.mof). |

*Force* \[in\]  
**true**, um das Entfernen der Konfiguration zu erzwingen.

## Rückgabewert
------------

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## Hinweise

Dies ist eine statische Methode.

## Anforderungen
------------
>**MOF:** DscCore.mof

>**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration


## Siehe auch


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->



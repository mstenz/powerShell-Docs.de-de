---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Starten der Konsistenzprüfung.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_performrequiredconfigurationchecks'
MSHAttr: 'PreferredLib:/library'
title: 'PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse'
---

# PerformRequiredConfigurationChecks-Methode der MSFT_DSCLocalConfigurationManager-Klasse

Startet eine Konsistenzprüfung unter Verwendung des Taskplaners.

Syntax
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

Parameter
----------

*Flags* \[in\]  
Eine Bitmaske, die den Typ der auszuführenden Konsistenzprüfung angibt. Die folgenden Werte sind gültig und können mit einem bitweisen **ODER**-Vorgang kombiniert werden:

|Wert |Beschreibung |
|:--- |:---|
|**1** | Eine normale Konsistenzprüfung. |
|**2** | Die Fortsetzung einer Konsistenzprüfung nach einem Neustart. Dieser Wert sollte nicht mit anderen Werten kombiniert werden. |
|**4** | Die Konfiguration sollte von dem Pull-Server abgerufen werden, der in der Metakonfiguration für den Knoten angegeben ist. Dieser Wert sollte immer mit **1** kombiniert werden, um einen Wert von **5** zu erzielen. |
|**8** | Senden des Status an den Berichtsserver. |

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


[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=Apr16_HO2-->



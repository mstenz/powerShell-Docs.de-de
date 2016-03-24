# Frequenzen für „RefreshMode“ und „ConfigurationMode“ müssen keine Vielfache des jeweils anderen sein

In der vorherigen Version von DSC behandelt der LCM `RefreshFrequencyMins` und `ConfigurationModeFrequencyMins` als Vielfaches des jeweils anderen (siehe die Erläuterung in diesem [Blog](http://blogs.msdn.com/b/powershell/archive/2013/12/09/understanding-meta-configuration-in-windows-powershell-desired-state-configuration.aspx)). In WMF 5.0 RTM werden diese Eigenschaften unabhängig voneinander verarbeitet. Die folgenden Tabellen veranschaulichen dieses Verhalten:

Verhalten im **PULL**-Modus: 

|                                  |**Wert in Metakonfiguration**|**Wert nach Anwenden der Metakonfiguration**|**Häufigkeit des Pullvorgangs (in Minuten)**|**Häufigkeit der Anwendung der Konfiguration (in Minuten)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |                                    |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |40                                  |                                                |

Verhalten im **PUSH**-Modus:

|                                  |**Wert in Metakonfiguration**|**Wert nach Anwenden der Metakonfiguration**|**Häufigkeit der Anwendung der Konfiguration (in Minuten)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |                                                |
<!--HONumber=Mar16_HO2-->

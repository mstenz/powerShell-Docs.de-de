# Trennung von Knoten- und Konfigurations-ID

## Übersicht

Um bei Verwenden von DSC im Pullmodus eine flexiblere und bessere Erfahrung zu bieten, haben wir in dieser Version verschiedene Features hinzugefügt. Diese Features ermöglichen Ihnen ein flexibles Einrichten und Bereitstellen von Konfigurationen auf mehreren Knoten und zugleich das Nachverfolgen des Status und von Berichtsinformationen für jeden einzelnen Knoten. Diese Features sind wie folgt:

* Ein Konfigurationsname, der die Konfiguration für einen Computer identifiziert. Dieser Name kann von mehreren Zielknoten verwendet werden. 
* Eine Agent-ID, die einen einzelnen Knoten eindeutig identifiziert.
* Ein Registrierungsschritt, der nur erfolgt, wenn sich ein Zielknoten erstmals mit einem Pullserver verbindet.

**Hinweis:** Diese Features und Funktionen wurden hinzugefügt und ersetzen vorhandene Pullfeatures und -konzepte nicht. Sie können diese neuen Features oder die älteren mit dem neuen Pullserver in dieser Version verwenden.

## Agent-ID

Diese Funktion ist für Benutzer gedacht, die nicht für jeden Zielknoten eindeutige Bezeichner einrichten und verwalten möchten. Die für das Verwalten von GUIDs erforderlichen Aufgaben sind also nicht mehr erforderlich. DSC generiert automatisch eine Agent-ID, die bei der Kommunikation mit dem Pullserver verwendet wird. Diese ID wird vom Pullserver verwendet, um alle Informationen für einen bestimmten Knoten eindeutig zu identifizieren. Dies bedeutet auch, dass Sie nicht jeden Knoten mit einer eindeutigen Metakonfiguration mit einer eindeutigen ID einrichten müssen. Folglich kann eine einzelne Metakonfiguration von vielen Zielknoten verwendet werden, wobei die eindeutige Identität jedes Knoten erhalten bleibt. 

## Konfigurationsname

Der Konfigurationsname ist der Anzeigename der Konfiguration, die auf einen Zielknoten angewendet wird. Die hiermit verbundenen Änderungen sind wie folgt:  

### Auswählen von Anzeigenamen

Der Anzeigename kann eine beliebige Zeichenfolge sein. Er muss nicht das Format einer GUID haben, weshalb eine Konfiguration zum Einrichten von SQL Server einfach „SQL_Server“ genannt werden kann. Dadurch kann der Zweck einer bestimmten Konfiguration einfacher bestimmt werden.

### Zuweisung

Die Konfiguration, die einem Knoten zugewiesen ist, wird auf dem Pullserver zentral verwaltet. Diese kann einem Bootstrapping unterzogen werden, indem die „ConfigrationName“-Eigenschaft in der Metakonfiguration definiert wird, die aber nur während der Registrierung verwendet wird. Nach der Registrierung informiert der Server den Zielknoten, welche Konfiguration er erhält. Für den lokalen Pullserver kann diese Zuordnung zwischen Konfigurationen und Zielknoten erst während der Registrierung erfolgen. Doch in Azure Automation können diese Änderung einfach über die Benutzeroberfläche oder die entsprechenden Cmdlets erfolgen. Sie können zum Ändern der Konfiguration des lokalen Pullservers, die einem Zielknoten zugewiesen ist, die Registrierung erneut ausführen.

### Mehrere bzw. Teilkonfigurationen

Wenn mehrere Konfigurationsnamen einem Zielknoten zugewiesen sind, werden sie wie Teilkonfigurationen behandelt. Damit dies funktioniert, muss die Metakonfiguration auf dem Zielknoten für das Akzeptieren von Teilkonfigurationen konfiguriert werden. **Hinweis:** Dies wird nur auf dem lokalen Pullserver unterstützt. Azure Automation unterstützt keine Teilkonfigurationen.

## Registrierung

Da Konfigurationsnamen keine GUIDs mehr, sondern nun Anzeigenamen sind, können Sie einfacher ermittelt werden. Zur Verringerung dieses inhärenten Sicherheitsproblems haben wir einen Registrierungsschritt hinzugefügt, bevor ein Knoten Konfigurationen von einem Server anfordern kann. Ein Knoten registriert sich selbst beim Pullserver mit einem gemeinsamen geheimen Schlüssel (den Knoten und Server bereits kennen) und optional dem Namen der Konfiguration, die er anfordert. Dieser gemeinsame geheime Schlüssel muss nicht für jeden Computer eindeutig sein. Angenommen, der gemeinsame geheime Schlüssel ist ein schwer zu erratender Bezeichner, wie z. B. eine GUID. Dieser gemeinsame geheime Schlüssel wird von der **RegistrationKey**-Eigenschaft in der Metakonfiguration des Zielknotens definiert.

### Beispiel einer Metakonfiguration

```powershell
[DscLocalConfigurationManager()]
Configuration SampleMetaConfig
{
    Settings
    {
        RefreshMode = "PULL";
        AllowModuleOverwrite = $true;
        RebootNodeIfNeeded = $true;
        ConfigurationModeFrequencyMins = 60;
    }

    ConfigurationRepositoryWeb ConfigurationManager
    {
        ServerURL = “https://PullServerMachine:8080/psdscpullserver.svc”
        RegistrationKey = "140a952b-b9d6-406b-b416-e0f759c9c0e4"
        ConfigurationNames = @(“WebRole”)
    }
}

SampleMetaConfig
```

Der „RegistrationKey“-Wert muss auf dem Pullserver definiert werden. Erstellen Sie dazu beim Einrichten des Pullservers eine Textdatei mit dem Namen **RegistrationKeys.txt** an einem bestimmten Speicherort, und legen Sie dann diesen Speicherort in der Datei „web.config“ des Pullservers fest (siehe unten).  

```XML
<add key="ConfigurationPath" value="C:\Program Files\WindowsPowerShell\DscService\Configuration">

<add key="ModulePath" value="C:\Program Files\WindowsPowerShell\DscService\Modules">

<add key="RegistrationKeyPath" value="C:\Program Files\WindowsPowerShell\DscService">
```

Verwenden Sie die neueste Version der DSC-Ressource „xDSCWebService“, um einen lokalen Pullserver vollständig für die Verwendung damit bereitzustellen. In der [Beispielkonfiguration](https://github.com/grayzu/PSSummitEU2015/blob/master/PullServer/02%20-%20PullServer%20Config.ps1) finden Sie eine vollständige Konfiguration.

**Hinweis:** Dieses Feature wird nicht unterstützt, wenn der Pullserver als Dateifreigabe eingerichtet ist. Es wird nur für webbasierte Pullserver unterstützt.

<!--HONumber=Mar16_HO2-->



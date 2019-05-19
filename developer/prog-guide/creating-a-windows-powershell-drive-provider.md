---
title: Erstellen eines Anbieters der Windows PowerShell-Laufwerk | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: 2696d78cae7739310b7684161b597ce436dabe92
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855207"
---
# <a name="creating-a-windows-powershell-drive-provider"></a>Erstellen eines Windows PowerShell-Laufwerkanbieters

Dieses Thema beschreibt, wie Sie einen Windows PowerShell-Laufwerk-Anbieter erstellen, der mit einen Datenspeicher über ein Windows PowerShell-Laufwerk zugreifen können. Dieser Typ des Anbieters ist auch als Windows PowerShell-Laufwerk-Anbieter bezeichnet. Die Windows PowerShell-Laufwerke, die vom Anbieter verwendeten bieten die Möglichkeit, eine Verbindung mit dem Datenspeicher herstellen.

Die hier beschriebene Windows PowerShell-Laufwerk-Anbieter bietet Zugriff auf eine Microsoft Access-Datenbank. Für diesen Anbieter, stellt das Windows PowerShell-Laufwerk (es ist möglich, eine beliebige Anzahl von Laufwerken zu einem laufwerksanbieter hinzufügen) die Datenbank dar, mit der Container der obersten Ebene des Laufwerks darstellen, die Tabellen in der Datenbank und die Elemente der Container stehen für die Zeilen in die Tabellen.

## <a name="defining-the-windows-powershell-provider-class"></a>Definieren der Windows PowerShell-Anbieter-Klasse

Die Laufwerk-Anbieter muss eine abgeleitete Klasse .NET definieren die [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Basisklasse. So sieht die Klassendefinition für dieses Laufwerk-Anbieter aus:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

Beachten Sie, dass in diesem Beispiel die [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) Attribut gibt an, einen benutzerfreundlichen Namen für den Anbieter und den Windows PowerShell-spezifischen Funktionen, die der Anbieter macht die Windows PowerShell-Laufzeit während der befehlsverarbeitung verfügbar. Die möglichen Werte für die Funktionen des Anbieters werden definiert, durch die [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) Enumeration. Dieses Laufwerk-Anbieter unterstützt keine dieser Funktionen.

## <a name="defining-base-functionality"></a>Definiert die grundlegenden Funktionen

Siehe [Entwurf der Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md), [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) Klasse leitet sich von der [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) Basisklasse, die die Methoden, die erforderlich sind, für das Initialisieren und zum Aufheben der Initialisierung des Anbieters definiert. Zum Implementieren der Funktionalität, die sitzungsspezifischen Initialisierungsinformationen hinzufügen und Freigeben von Ressourcen, die vom Anbieter verwendet werden, finden Sie unter [erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md). Allerdings können die meisten Anbieter (einschließlich des hier beschriebenen Anbieters) die standardmäßige Implementierung dieser Funktionalität, die von Windows PowerShell bereitgestellt wird.

## <a name="creating-drive-state-information"></a>Erstellen von Laufwerkstatus-Informationen

Alle Windows PowerShell-Anbieter werden statusfrei sein, berücksichtigt, was bedeutet, dass es sich bei Ihrem laufwerksanbieter muss alle Zustandsinformationen zu erstellen, die von der Windows PowerShell-Laufzeit benötigt wird, wenn Ihr Anbieter aufgerufen.

Für diesen laufwerksanbieter enthält Zustandsinformationen für die Verbindung mit der Datenbank, die als Teil der Informationen zum Laufwerk gespeichert wird. Hier ist der Code, der zeigt, wie diese Informationen gespeichert werden, in der [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt, das Laufwerk beschreibt:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a>Erstellen ein Laufwerk

Damit wird die Windows PowerShell-Laufzeit, um ein Laufwerk zu erstellen, muss die Laufwerk-Anbieter implementieren die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode. Der folgende Code zeigt die Implementierung der [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) Methode für diesen laufwerksanbieter:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

Ihre Überschreibung der diese Methode sollte folgendermaßen vor:

- Überprüfen Sie, ob die [System.Management.Automation.PSDriveinfo.Root*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) Element vorhanden ist und, die eine Verbindung mit dem Datenspeicher hergestellt werden kann.

- Erstellen Sie ein Laufwerk, und füllen Sie das Verbindung-Mitglied, Unterstützung des der `New-PSDrive` Cmdlet.

- Überprüfen Sie die [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) -Objekt für das vorgeschlagene Laufwerk.

- Ändern der [: System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) Objekt, das Laufwerk mit allen erforderlichen Leistung oder Zuverlässigkeit Informationen beschreibt, oder geben Sie zusätzliche Daten, für das Laufwerk mit Aufrufer.

- Behandeln von Fehlern, die mit der [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) Methode, und klicken Sie dann geben `null`.

  Diese Methode gibt die Laufwerkinformationen, die übergeben wurde, auf die Methode oder eine anbieterspezifische-Version des Zertifikats.

## <a name="attaching-dynamic-parameters-to-newdrive"></a>Dynamische Parameter anfügen NewDrive

Die `New-PSDrive` Cmdlets, die von Ihrem laufwerksanbieter unterstützt möglicherweise zusätzliche Parameter. Um diese dynamischen Parameter an das Cmdlet anzufügen, die den Anbieter implementiert die [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) Methode. Diese Methode gibt ein Objekt mit Eigenschaften und Felder mit der Analyse der Attributen ähnelt einer Cmdlet-Klasse oder ein [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) Objekt.

Dieses Laufwerk-Anbieter überschreibt diese Methode nicht. Der folgende Code zeigt jedoch die Standardimplementierung dieser Methode:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a>Entfernen ein Laufwerk

Zum Schließen der Verbindung mit der der laufwerksanbieter implementieren muss die [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode. Diese Methode schließt die Verbindung auf das Laufwerk nach dem Bereinigen alle Anbieter-spezifischen Informationen.

Der folgende Code zeigt die Implementierung der [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) Methode für diesen laufwerksanbieter:

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

Wenn das Laufwerk entfernt werden kann, sollte die Methode über an die Methode übergebenen Informationen zurückgeben der `drive` Parameter. Wenn das Laufwerk kann nicht entfernt werden, die Methode eine Ausnahme schreiben und dann zurückkehren soll `null`. Wenn Ihr Anbieter diese Methode nicht überschreibt, gibt die Standardimplementierung dieser Methode nur die Laufwerkinformationen, die als Eingabe übergeben.

## <a name="initializing-default-drives"></a>Initialisieren von Standard-Laufwerke

Die Laufwerk-Anbieter implementiert die [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) Methode, um die Laufwerke bereitstellen. Active Directory-Anbieter stellen z. B. kann ein Laufwerk für den Standardnamenskontext, wenn der Computer einer Domäne angehört.

Diese Methode gibt eine Auflistung von Laufwerkinformationen zu den initialisierten Laufwerken oder eine leere Auflistung zurück. Der Aufruf dieser Methode erfolgt nach dem Aufrufen der Windows PowerShell-Laufzeit die [System.Management.Automation.Provider.Cmdletprovider.Start*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) Methode, um den Anbieter zu initialisieren.

Dieses Laufwerk-Anbieter überschreibt nicht die [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) Methode. Der folgende Code zeigt jedoch die Standardimplementierung, die eine leeres Laufwerk Auflistung zurückgibt:

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a>Punkte zu beachten, die zum Implementieren von InitializeDefaultDrives

Alle Laufwerk-Anbieter sollte ein Stammlaufwerk, die der Benutzer mit Erkennbarkeit helfen bereitstellen. Das Stammlaufwerk möglicherweise Standorte aufzulisten, die als Stämme für andere bereitgestellten Laufwerken dienen. Active Directory-Anbieter kann beispielsweise ein Laufwerk, das listet Namenskontexte finden Sie im Erstellen der `namingContext` Attribute für den Stamm verteilte Umgebung (DSE). Dadurch können Benutzer, die Bereitstellungspunkte für andere Laufwerke zu ermitteln.

## <a name="code-sample"></a>Codebeispiel

Vollständigen Beispielcode finden Sie unter [AccessDbProviderSample02 Codebeispiel](./accessdbprovidersample02-code-sample.md).

## <a name="testing-the-windows-powershell-drive-provider"></a>Testen des Anbieters der Windows PowerShell-Laufwerk

Wenn Ihre Windows PowerShell-Anbieter mit Windows PowerShell registriert wurde, können Sie es testen, durch Ausführen der unterstützten Cmdlets in der Befehlszeile, einschließlich alle Cmdlets, die durch Ableitung zur Verfügung gestellt. Testen Sie nun den laufwerksanbieter Beispiel.

1. Führen Sie die `Get-PSProvider` -Cmdlet zum Abrufen der Liste der Anbieter, um sicherzustellen, dass es sich bei der laufwerksanbieter AccessDB vorhanden ist:

   **PS> `Get-PSProvider`**

   Die folgende Ausgabe wird angezeigt:

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. Stellen Sie sicher, dass für die Datenbank ein Datenbank-Servernamen (DSN) vorhanden ist, durch den Zugriff auf die **Datenquellen** Teil der **Verwaltung** für das Betriebssystem. In der **Benutzer-DSN** table, doppelklicken Sie auf **MS Access-Datenbank** und den Pfad zum Laufwerk C:\ps\northwind.mdb hinzufügen.

3. Erstellen Sie ein neues Laufwerk, das mit dem Beispiel Laufwerk-Anbieter:

   **PS > Neues Psdrive-Namen Mydb-root-c:\ps\northwind.mdb - Psprovider AccessDb**

   Die folgende Ausgabe wird angezeigt:

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. Überprüfen der Verbindung an. Da die Verbindung als Mitglied des Laufwerks definiert ist, können Sie es mit dem Cmdlet Get-PDDrive überprüfen.

   > [!NOTE]
   > Der Benutzer kann nicht mit dem Anbieter als Laufwerk noch interagieren, wie der Anbieter Containerfunktionalität für diese Interaktion benötigt. Weitere Informationen finden Sie unter [erstellen eine Windows PowerShell-Containeranbieter](./creating-a-windows-powershell-container-provider.md).

   **PS > (Get-Psdrive Mydb) .connection**

   Die folgende Ausgabe wird angezeigt:

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. Entfernen Sie das Laufwerk, und beenden Sie die Shell aus:

   **PS > Remove-Psdrive Mydb**

   **PS > Beenden**

## <a name="see-also"></a>Weitere Informationen

[Erstellen von Windows PowerShell-Anbieter](./how-to-create-a-windows-powershell-provider.md)

[Entwerfen Sie Ihre Windows PowerShell-Anbieter](./designing-your-windows-powershell-provider.md)

[Erstellen einen einfachen Windows PowerShell-Anbieter](./creating-a-basic-windows-powershell-provider.md)
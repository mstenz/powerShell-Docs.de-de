---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
title: Katalog-Cmdlets
ms.openlocfilehash: f0869e8c174ab127996866775ad20d056f877345
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="catalog-cmdlets"></a>Katalog-Cmdlets  

Dem [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx)-Modul wurden zwei neue Cmdlets hinzugefügt. Sie generieren und überprüfen Windows-Katalogdateien.  

## <a name="new-filecatalog"></a>New-FileCatalog 
--------------------------------

`New-FileCatalog` erstellt eine Windows-Katalogdatei für eine Gruppe von Ordnern und Dateien. Eine Katalogdatei enthält die Hashes aller Dateien in bestimmten Pfaden. Benutzer können den Satz von Ordnern zusammen mit den entsprechenden Katalogdateien verteilen, die diese Ordner darstellen. Eine Katalogdatei kann vom Empfänger des Inhalts verwendet werden, um zu überprüfen, ob an den Ordnern Änderungen vorgenommen wurden, nachdem der Katalog erstellt wurde.    

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Unterstützt wird die Erstellung von Katalogversion 1 und 2. Version 1 verwendet den SHA1-Hashalgorithmus, um Dateihashes zu erstellen, Version 2 verwendet SHA256. Katalogversion 2 wird weder auf *Windows Server 2008 R2* noch auf *Windows 7* unterstützt. Es wird empfohlen, Katalogversion 2 zu verwenden, wenn Sie Plattformen wie *Windows 8*, *Windows Server 2012* und höher nutzen.  

Wenn Sie diesen Befehl auf ein bestehendes Modul anwenden möchten, müssen Sie die Variablen CatalogFilePath und Path gemäß des Speicherorts des Modulmanifests angeben. Im nachstehenden Beispiel ist das Modulmanifest unter „C:\Program Files\Windows PowerShell\Modules\Pester“ gespeichert. 

![](../images/NewFileCatalog.jpg)

Dadurch wird die Katalogdatei erstellt. 

![](../images/CatalogFile1.jpg)  

![](../images/CatalogFile2.jpg) 

Die Katalogdatei (im obigen Beispiel: „pester.cat“) muss mit dem Cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx) signiert werden, um ihre Integrität zu überprüfen.   


## <a name="test-filecatalog"></a>Test-FileCatalog 
--------------------------------

`Test-FileCatalog` überprüft den Katalog, der einen Satz von Ordnern darstellt. 

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Dieses Cmdlet vergleicht die Hashes aller Dateien und deren relative Pfade in der Katalogdatei mit denen, die auf dem Datenträger gespeichert sind. Wenn das Cmdlet eine Unstimmigkeit zwischen den Dateihashes und den Pfaden entdeckt, gibt es den Status `ValidationFailed` zurück. Benutzer können alle diese Informationen mithilfe des Schalters `Detailed` abrufen. Der Signierstatus des Katalogs wird im Feld `Signature` angezeigt, was dem Aufrufen des Cmdlets [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) für die Katalogdatei entspricht. Benutzer können außerdem jede Datei während der Überprüfung mithilfe des Parameters `FilesToSkip` überspringen. 


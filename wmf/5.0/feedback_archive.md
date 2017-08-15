---
ms.date: 2017-06-12T00:00:00.000Z
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 7ad4a00f7beba0de70696d88cd5448c7c638c50c
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/27/2017
---
# <a name="archive-cmdlets"></a>„Archive“-Cmdlets

Die beiden neuen Cmdlets **Compress-Archive** und **Expand-Archive** ermöglichen das Komprimieren und Dekomprimieren von ZIP-Dateien.

## <a name="compress-archive"></a>Compress-Archive
Das Cmdlet **Compress-Archive** erstellt aus angegebenen Dateien eine neue Archivdatei. Eine Archivdatei ermöglicht für eine einfachere Handhabung und Speicherung das Zusammenfassen mehrerer Dateien zu einem komprimierbaren Paket. Eine Archivdatei kann mithilfe eines Komprimierungsalgorithmus komprimiert werden, der im **-CompressionLevel**-Parameter angegeben wird.
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a>Expand-Archive
Das Cmdlet **Expand-Archive** extrahiert Dateien aus einer angegebenen Archivdatei. Eine Archivdatei ermöglicht für eine einfachere Handhabung und Speicherung das Zusammenfassen mehrerer Dateien zu einem komprimierbaren Paket.
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```


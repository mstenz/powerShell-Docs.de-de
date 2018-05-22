---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
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

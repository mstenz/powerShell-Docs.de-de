---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 9ca12ad3f0729a2e9595d7ca5ccf9041e47658a3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218092"
---
# <a name="archive-cmdlets"></a><span data-ttu-id="2d63f-102">„Archive“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="2d63f-102">Archive cmdlets</span></span>

<span data-ttu-id="2d63f-103">Die beiden neuen Cmdlets **Compress-Archive** und **Expand-Archive** ermöglichen das Komprimieren und Dekomprimieren von ZIP-Dateien.</span><span class="sxs-lookup"><span data-stu-id="2d63f-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="2d63f-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="2d63f-104">Compress-Archive</span></span>
<span data-ttu-id="2d63f-105">Das Cmdlet **Compress-Archive** erstellt aus angegebenen Dateien eine neue Archivdatei.</span><span class="sxs-lookup"><span data-stu-id="2d63f-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="2d63f-106">Eine Archivdatei ermöglicht für eine einfachere Handhabung und Speicherung das Zusammenfassen mehrerer Dateien zu einem komprimierbaren Paket.</span><span class="sxs-lookup"><span data-stu-id="2d63f-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="2d63f-107">Eine Archivdatei kann mithilfe eines Komprimierungsalgorithmus komprimiert werden, der im **-CompressionLevel**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="2d63f-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```powershell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="2d63f-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="2d63f-108">Expand-Archive</span></span>
<span data-ttu-id="2d63f-109">Das Cmdlet **Expand-Archive** extrahiert Dateien aus einer angegebenen Archivdatei.</span><span class="sxs-lookup"><span data-stu-id="2d63f-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="2d63f-110">Eine Archivdatei ermöglicht für eine einfachere Handhabung und Speicherung das Zusammenfassen mehrerer Dateien zu einem komprimierbaren Paket.</span><span class="sxs-lookup"><span data-stu-id="2d63f-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```powershell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```

---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d23cfc2aaa680c247aaab91d8875c64c9d62187e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="archive-cmdlets"></a><span data-ttu-id="c3ea3-102">„Archive“-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="c3ea3-102">Archive cmdlets</span></span>

<span data-ttu-id="c3ea3-103">Die beiden neuen Cmdlets **Compress-Archive** und **Expand-Archive** ermöglichen das Komprimieren und Dekomprimieren von ZIP-Dateien.</span><span class="sxs-lookup"><span data-stu-id="c3ea3-103">Two new cmdlets, **Compress-Archive** and **Expand-Archive**, let you compress and expand ZIP files.</span></span>

## <a name="compress-archive"></a><span data-ttu-id="c3ea3-104">Compress-Archive</span><span class="sxs-lookup"><span data-stu-id="c3ea3-104">Compress-Archive</span></span>
<span data-ttu-id="c3ea3-105">Das Cmdlet **Compress-Archive** erstellt aus angegebenen Dateien eine neue Archivdatei.</span><span class="sxs-lookup"><span data-stu-id="c3ea3-105">The **Compress-Archive** cmdlet creates a new archive file from specified files.</span></span> <span data-ttu-id="c3ea3-106">Eine Archivdatei ermöglicht für eine einfachere Handhabung und Speicherung das Zusammenfassen mehrerer Dateien zu einem komprimierbaren Paket.</span><span class="sxs-lookup"><span data-stu-id="c3ea3-106">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span> <span data-ttu-id="c3ea3-107">Eine Archivdatei kann mithilfe eines Komprimierungsalgorithmus komprimiert werden, der im **-CompressionLevel**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="c3ea3-107">An archive file can be compressed by using a compression algorithm specified in the **-CompressionLevel** parameter.</span></span>
```PowerShell
Compress-Archive -LiteralPath <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>] 
Compress-Archive [-Path] <String[]> [-DestinationPath] <String> [-Update] [-CompressionLevel <Microsoft.PowerShell.Commands.CompressionLevel>]
```

## <a name="expand-archive"></a><span data-ttu-id="c3ea3-108">Expand-Archive</span><span class="sxs-lookup"><span data-stu-id="c3ea3-108">Expand-Archive</span></span>
<span data-ttu-id="c3ea3-109">Das Cmdlet **Expand-Archive** extrahiert Dateien aus einer angegebenen Archivdatei.</span><span class="sxs-lookup"><span data-stu-id="c3ea3-109">The **Expand-Archive** cmdlet extracts files from a specified archive file.</span></span> <span data-ttu-id="c3ea3-110">Eine Archivdatei ermöglicht für eine einfachere Handhabung und Speicherung das Zusammenfassen mehrerer Dateien zu einem komprimierbaren Paket.</span><span class="sxs-lookup"><span data-stu-id="c3ea3-110">An archive file allows multiple files to be packaged and optionally compressed into a single file for easier handling and storage.</span></span>
```PowerShell
Expand-Archive -LiteralPath <String> [-DestinationPath] <String>
Expand-Archive [-Path] <String> [-DestinationPath] <String>
```


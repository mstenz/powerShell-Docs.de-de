---
title: Vorgehensweise beim Testen der aktualisierbaren Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367149"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="57be2-102">Testen der aktualisierbaren Hilfe</span><span class="sxs-lookup"><span data-stu-id="57be2-102">How to Test Updatable Help</span></span>

<span data-ttu-id="57be2-103">In diesem Thema werden die Ansätze zum Testen der aktualisierbaren Hilfe für ein Modul beschrieben.</span><span class="sxs-lookup"><span data-stu-id="57be2-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="57be2-104">Verwenden von Verbose zum Erkennen von Fehlern</span><span class="sxs-lookup"><span data-stu-id="57be2-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="57be2-105">Nachdem Sie die helpinfo-XML-Datei und die CAB-Dateien für das Modul hochgeladen haben, testen Sie die Dateien, indem Sie einen [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Befehl mit dem Parameter **verbose** ausführen</span><span class="sxs-lookup"><span data-stu-id="57be2-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="57be2-106">Der **verbose** -Parameter weist `Update-Help` an, die wichtigen Schritte in seinen Aktionen zu melden, von dem Lesen des **helpinfouri** -Schlüssels im Modul Manifest zum Überprüfen der Dateitypen in der entpackten CAB-Datei und Ablegen der Dateien in der sprachspezifischen Modul Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="57be2-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="57be2-107">Wenn alle ausführlichen Meldungen aufgelöst werden, führen Sie den Befehl "`Update-Help`" mit dem Parameter " **Debug** " aus.</span><span class="sxs-lookup"><span data-stu-id="57be2-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="57be2-108">Dieser Parameter sollte alle verbleibenden Probleme mit den aktualisierbaren Hilfedateien erkennen.</span><span class="sxs-lookup"><span data-stu-id="57be2-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
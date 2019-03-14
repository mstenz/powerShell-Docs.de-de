---
title: So testen Sie die aktualisierbare Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e064048-2b94-4365-bdb7-f1ee7c0a7fd7
caps.latest.revision: 6
ms.openlocfilehash: cecc6c26ccaece06462ddd74b53534137fcf3037
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794262"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="3f82f-102">Testen der aktualisierbaren Hilfe</span><span class="sxs-lookup"><span data-stu-id="3f82f-102">How to Test Updatable Help</span></span>

<span data-ttu-id="3f82f-103">Dieses Thema beschreibt Verfahren zum Testen der aktualisierbaren Hilfe für ein Modul.</span><span class="sxs-lookup"><span data-stu-id="3f82f-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="3f82f-104">Verwenden ausführliche Fehler zu erkennen</span><span class="sxs-lookup"><span data-stu-id="3f82f-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="3f82f-105">Testen Sie die Dateien nach dem Hochladen der HelpInfo XML-Datei und die CAB-Dateien für das Modul mit einer [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) -Befehl mit der **ausführlich** Parameter.</span><span class="sxs-lookup"><span data-stu-id="3f82f-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="3f82f-106">Die **ausführlich** -Parameter weist `Update-Help` melden die wichtigen Schritte in der Liste der Vorgänge beim Lesen der **HelpInfoUri** -Schlüssels im modulmanifest zur Überprüfung der Dateitypen in die entpackten CAB-Datei ein, und platzieren die Dateien in sprachspezifischen Modulverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="3f82f-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="3f82f-107">Wenn Sie alle ausführliche Meldungen aufgelöst werden, führen Sie eine `Update-Help` -Befehl mit der **Debuggen** Parameter.</span><span class="sxs-lookup"><span data-stu-id="3f82f-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="3f82f-108">Dieser Parameter sollte alle verbleibenden Probleme mit aktualisierbaren Hilfedateien erkennen.</span><span class="sxs-lookup"><span data-stu-id="3f82f-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
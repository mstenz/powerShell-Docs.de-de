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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082327"
---
# <a name="how-to-test-updatable-help"></a><span data-ttu-id="496ba-102">Testen der aktualisierbaren Hilfe</span><span class="sxs-lookup"><span data-stu-id="496ba-102">How to Test Updatable Help</span></span>

<span data-ttu-id="496ba-103">Dieses Thema beschreibt Verfahren zum Testen der aktualisierbaren Hilfe für ein Modul.</span><span class="sxs-lookup"><span data-stu-id="496ba-103">This topic describes approaches to testing Updatable Help for a module.</span></span>

## <a name="using-verbose-to-detect-errors"></a><span data-ttu-id="496ba-104">Verwenden ausführliche Fehler zu erkennen</span><span class="sxs-lookup"><span data-stu-id="496ba-104">Using Verbose to Detect Errors</span></span>

<span data-ttu-id="496ba-105">Testen Sie die Dateien nach dem Hochladen der HelpInfo XML-Datei und die CAB-Dateien für das Modul mit einer [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) -Befehl mit der **ausführlich** Parameter.</span><span class="sxs-lookup"><span data-stu-id="496ba-105">After uploading the HelpInfo XML file and CAB files for your module, test the files by running an [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) command with the **Verbose** parameter.</span></span> <span data-ttu-id="496ba-106">Die **ausführlich** -Parameter weist `Update-Help` melden die wichtigen Schritte in der Liste der Vorgänge beim Lesen der **HelpInfoUri** -Schlüssels im modulmanifest zur Überprüfung der Dateitypen in die entpackten CAB-Datei ein, und platzieren die Dateien in sprachspezifischen Modulverzeichnis gespeichert.</span><span class="sxs-lookup"><span data-stu-id="496ba-106">The **Verbose** parameter directs `Update-Help` to report the critical steps in its actions, from reading the **HelpInfoUri** key in the module manifest to validating the file types in the unpacked CAB file and placing the files in the language-specific module directory.</span></span>

<span data-ttu-id="496ba-107">Wenn Sie alle ausführliche Meldungen aufgelöst werden, führen Sie eine `Update-Help` -Befehl mit der **Debuggen** Parameter.</span><span class="sxs-lookup"><span data-stu-id="496ba-107">When all verbose messages are resolved, run an `Update-Help` command with the **Debug** parameter.</span></span> <span data-ttu-id="496ba-108">Dieser Parameter sollte alle verbleibenden Probleme mit aktualisierbaren Hilfedateien erkennen.</span><span class="sxs-lookup"><span data-stu-id="496ba-108">This parameter should detect any remaining problems with the Updatable Help files.</span></span>
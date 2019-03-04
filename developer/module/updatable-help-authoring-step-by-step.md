---
title: 'Aktualisierbare Hilfeerstellung: Schrittweise | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860316"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="99b53-102">Aktualisierbare Hilfeerstellung: Ausführliche Anleitung</span><span class="sxs-lookup"><span data-stu-id="99b53-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="99b53-103">Diese Dokumente sind die Schritte im Erstellen von aktualisierbaren Hilfe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="99b53-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="99b53-104">Erstellen aktualisierbare Hilfe: Ausführliche Anleitung</span><span class="sxs-lookup"><span data-stu-id="99b53-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="99b53-105">Aktualisierbare Hilfe ist für Endbenutzer ausgelegt, aber bietet auch bedeutende Vorteile, modulautoren und Hilfe Schreibern stammen, einschließlich der Möglichkeit zum Hinzufügen von Inhalt, Beheben von Fehlern, Bereitstellen in mehreren Benutzeroberflächenkulturen und reagieren auf Kommentare von Benutzern und Anforderungen, lange dauert es nach der Modul wurde versandt.</span><span class="sxs-lookup"><span data-stu-id="99b53-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="99b53-106">In diesem Thema wird erläutert, wie Sie verpacken und Hochladen-Hilfedateien, damit Benutzer herunterladen und installieren Sie sie mithilfe von können die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="99b53-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="99b53-107">Die folgenden Schritte bieten einen Überblick über den Prozess der Unterstützung der aktualisierbaren Hilfe.</span><span class="sxs-lookup"><span data-stu-id="99b53-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="99b53-108">„Schritt 1: Suchen einer Internetsite für Ihre Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="99b53-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="99b53-109">Der erste Schritt beim Erstellen von aktualisierbaren Hilfe ist finden Sie einen Speicherort im Internet nach Hilfedateien des Moduls.</span><span class="sxs-lookup"><span data-stu-id="99b53-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="99b53-110">Tatsächlich können Sie zwei verschiedene Speicherorten.</span><span class="sxs-lookup"><span data-stu-id="99b53-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="99b53-111">Sie können an einem Speicherort im Internet und die Hilfe Content-CAB-Dateien auf einem anderen Speicherort im Internet des Moduls hilfeinformationsdatei (HelpInfo XML - unten beschrieben) beibehalten.</span><span class="sxs-lookup"><span data-stu-id="99b53-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="99b53-112">Alle Inhalte CAB Hilfedateien für ein Modul müssen sich am gleichen Standort sein.</span><span class="sxs-lookup"><span data-stu-id="99b53-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="99b53-113">Sie können Hilfe Inhalte CAB-Dateien für unterschiedliche Module am gleichen Speicherort platzieren.</span><span class="sxs-lookup"><span data-stu-id="99b53-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="99b53-114">Schritt 2: Fügen Sie einen HelpInfoURI-Schlüssel zu Ihrem modulmanifest</span><span class="sxs-lookup"><span data-stu-id="99b53-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="99b53-115">Hinzufügen einer **HelpInfoURI** Schlüssel zu Ihrem modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="99b53-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="99b53-116">Der Wert des Schlüssels ist der Uniform Resource Identifier (URI) des Speicherorts der HelpInfo XML-Informationsdatei für Ihr Modul.</span><span class="sxs-lookup"><span data-stu-id="99b53-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="99b53-117">Aus Sicherheitsgründen muss die Adresse mit "http" oder "Https" beginnen.</span><span class="sxs-lookup"><span data-stu-id="99b53-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="99b53-118">Der URI sollte einen Speicherort im Internet angeben, aber Sie dürfen keine der HelpInfo XML-Dateiname.</span><span class="sxs-lookup"><span data-stu-id="99b53-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="99b53-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="99b53-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="99b53-120">Schritt 3: Erstellen Sie eine HelpInfo XML-Datei</span><span class="sxs-lookup"><span data-stu-id="99b53-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="99b53-121">Die HelpInfo XML-Informationsdatei enthält den URI, von dem Speicherort im Internet die Hilfedateien und die Versionsnummern der neuesten Hilfedateien für das Modul in jede unterstützte Benutzeroberflächenkultur an.</span><span class="sxs-lookup"><span data-stu-id="99b53-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="99b53-122">Alle Windows PowerShell-Modul verfügt über eine HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="99b53-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="99b53-123">Wenn Sie die Hilfedateien aktualisieren, wird Sie bearbeiten oder Ersetzen Sie die HelpInfo XML-Datei; Fügen Sie eine andere nicht.</span><span class="sxs-lookup"><span data-stu-id="99b53-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="99b53-124">Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen einer HelpInfo-XML-Datei](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="99b53-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="99b53-125">Schritt 4: Signieren Sie die Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="99b53-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="99b53-126">Digitale Signaturen sind nicht erforderlich, aber sie sind eine optimale Empfehlung, wenn Sie Dateien gemeinsam nutzen.</span><span class="sxs-lookup"><span data-stu-id="99b53-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="99b53-127">Schritt 5: Erstellen der CAB-Dateien</span><span class="sxs-lookup"><span data-stu-id="99b53-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="99b53-128">Verwenden Sie ein Tool, erstellt der CAB-Dateien wie MakeCab.exe, zum Erstellen, einer. CAB-Datei, die die Hilfedateien für das Modul enthält.</span><span class="sxs-lookup"><span data-stu-id="99b53-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="99b53-129">Erstellen Sie eine separate CAB-Datei für die Hilfedateien in jede unterstützte Benutzeroberflächenkultur an.</span><span class="sxs-lookup"><span data-stu-id="99b53-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="99b53-130">Weitere Informationen finden Sie unter [vorbereiten aktualisierbare Hilfe CAB-Dateien wie](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="99b53-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="99b53-131">Schritt 6: Hochladen von Dateien</span><span class="sxs-lookup"><span data-stu-id="99b53-131">Step 6: Upload your files</span></span>

<span data-ttu-id="99b53-132">Um neue oder aktualisierte Hilfedateien zu veröffentlichen, Hochladen von CAB-Dateien auf dem Speicherort im Internet, die angegeben wird die **HelpContentUri** Element in der HelpInfo XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="99b53-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="99b53-133">Klicken Sie dann die HelpInfo XML-Datei hochladen, zu dem Speicherort im Internet, die durch den Wert der angegebenen die **HelpInfoUri** -Schlüssels im modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="99b53-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>

---
title: 'Aktualisierbare Hilfe Erstellung: Schritt für Schritt | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366989"
---
# <a name="updatable-help-authoring-step-by-step"></a><span data-ttu-id="99181-102">Aktualisierbare Hilfeerstellung: Schrittanleitung</span><span class="sxs-lookup"><span data-stu-id="99181-102">Updatable Help Authoring: Step-by-Step</span></span>

<span data-ttu-id="99181-103">In diesem Dokument sind die Schritte zum Erstellen der aktualisierbaren Hilfe aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="99181-103">This documents lists the steps in the process of authoring Updatable Help.</span></span>

## <a name="authoring-updatable-help-step-by-step"></a><span data-ttu-id="99181-104">Erstellen aktualisierbarer Hilfe: Schritt für Schritt</span><span class="sxs-lookup"><span data-stu-id="99181-104">Authoring Updatable Help: Step-by-Step</span></span>

<span data-ttu-id="99181-105">Aktualisierbare Hilfe ist für Endbenutzer konzipiert, bietet aber auch bedeutende Vorteile für Modul Autoren und Unterstützung von Writern, einschließlich der Möglichkeit, Inhalte hinzuzufügen, Fehler zu beheben, in mehreren Benutzeroberflächen Kulturen zu liefern und auf Benutzerkommentare und-Anforderungen zu reagieren. Das Modul wurde ausgeliefert.</span><span class="sxs-lookup"><span data-stu-id="99181-105">Updatable Help is designed for end-users, but it also provides significant benefits to module authors and help writers, including the ability to add content, fix errors, deliver in multiple UI cultures, and respond to user comments and requests, long after the module has shipped.</span></span> <span data-ttu-id="99181-106">In diesem Thema wird erläutert, wie Sie Hilfedateien Verpacken und hochladen, damit Benutzer diese mithilfe der Cmdlets [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) herunterladen und installieren können.</span><span class="sxs-lookup"><span data-stu-id="99181-106">This topic explains how you package and upload help files so that users can download and install them by using the [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets.</span></span>

<span data-ttu-id="99181-107">Die folgenden Schritte bieten einen Überblick über den Prozess der Unterstützung der aktualisierbaren Hilfe.</span><span class="sxs-lookup"><span data-stu-id="99181-107">The following steps provide an overview of the process of supporting Updatable Help.</span></span>

### <a name="step-1-find-an-internet-site-for-your-help-files"></a><span data-ttu-id="99181-108">Schritt 1: Suchen einer Internet Website für Ihre Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="99181-108">Step 1: Find an Internet site for your help files</span></span>

<span data-ttu-id="99181-109">Der erste Schritt bei der Erstellung der aktualisierbaren Hilfe ist die Suche nach einem Internet Speicherort für die Hilfedateien Ihres Moduls.</span><span class="sxs-lookup"><span data-stu-id="99181-109">The first step in creating updatable help is to find an Internet location for your module's help files.</span></span> <span data-ttu-id="99181-110">Tatsächlich können Sie zwei verschiedene Speicherorte verwenden.</span><span class="sxs-lookup"><span data-stu-id="99181-110">Actually, you can use two different locations.</span></span> <span data-ttu-id="99181-111">Sie können die Hilfe Informationsdatei Ihres Moduls (helpinfo XML-beschrieben unten) an einem Internet Speicherort und den Hilfe Inhalts-CAB-Dateien an einem anderen Internet Speicherort aufbewahren.</span><span class="sxs-lookup"><span data-stu-id="99181-111">You can keep your module's help information file (HelpInfo XML - described below) at one Internet location and the help content CAB files at another Internet location.</span></span> <span data-ttu-id="99181-112">Alle Hilfe Inhalts-CAB-Dateien für ein Modul müssen sich am gleichen Speicherort befinden.</span><span class="sxs-lookup"><span data-stu-id="99181-112">All help content CAB files for a module must be in the same location.</span></span> <span data-ttu-id="99181-113">Sie können Hilfe Inhalts-CAB-Dateien für verschiedene Module am gleichen Speicherort platzieren.</span><span class="sxs-lookup"><span data-stu-id="99181-113">You can place help content CAB files for different modules in the same location.</span></span>

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a><span data-ttu-id="99181-114">Schritt 2: Hinzufügen eines helpinfouri-Schlüssels zum Modul Manifest</span><span class="sxs-lookup"><span data-stu-id="99181-114">Step 2: Add a HelpInfoURI key to your module manifest</span></span>

<span data-ttu-id="99181-115">Fügen Sie dem Modul Manifest einen **helpinfouri** -Schlüssel hinzu.</span><span class="sxs-lookup"><span data-stu-id="99181-115">Add a **HelpInfoURI** key to your module manifest.</span></span> <span data-ttu-id="99181-116">Der Wert des Schlüssels ist die Uniform Resource Identifier (URI) des Speicher Orts der helpinfo-XML-Informationsdatei für das Modul.</span><span class="sxs-lookup"><span data-stu-id="99181-116">The value of the key is the Uniform Resource Identifier (URI) of the location of the HelpInfo XML information file for your module.</span></span> <span data-ttu-id="99181-117">Aus Sicherheitsgründen muss die Adresse mit "http" oder "https" beginnen.</span><span class="sxs-lookup"><span data-stu-id="99181-117">For security, the address must begin with "http" or "https".</span></span> <span data-ttu-id="99181-118">Der URI sollte einen Internet Speicherort angeben, darf jedoch nicht den Namen der helpinfo-XML-Datei enthalten.</span><span class="sxs-lookup"><span data-stu-id="99181-118">The URI should specify an Internet location, but must not include the HelpInfo XML file name.</span></span>

<span data-ttu-id="99181-119">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="99181-119">For example:</span></span>

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a><span data-ttu-id="99181-120">Schritt 3: Erstellen einer helpinfo-XML-Datei</span><span class="sxs-lookup"><span data-stu-id="99181-120">Step 3: Create a HelpInfo XML file</span></span>

<span data-ttu-id="99181-121">Die helpinfo-XML-Informationsdatei enthält den URI des Internet Speicherorts ihrer Hilfedateien und die Versionsnummern der neuesten Hilfedateien für das Modul in jeder unterstützten Benutzeroberflächen Kultur.</span><span class="sxs-lookup"><span data-stu-id="99181-121">The HelpInfo XML information file contains the URI of the Internet location of your help files and the version numbers of the newest help files for your module in each supported UI culture.</span></span> <span data-ttu-id="99181-122">Jedes Windows PowerShell-Modul verfügt über eine helpinfo-XML-Datei.</span><span class="sxs-lookup"><span data-stu-id="99181-122">Every Windows PowerShell module has one HelpInfo XML file.</span></span> <span data-ttu-id="99181-123">Wenn Sie die Hilfedateien aktualisieren, müssen Sie die helpinfo-XML-Datei bearbeiten oder ersetzen. Sie fügen keinen weiteren hinzu.</span><span class="sxs-lookup"><span data-stu-id="99181-123">When you update your help files, you edit or replace the HelpInfo XML file; you do not add another one.</span></span> <span data-ttu-id="99181-124">Weitere Informationen finden Sie unter [Erstellen einer helpinfo-XML-Datei](./how-to-create-a-helpinfo-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="99181-124">For more information, see [How to Create a HelpInfo XML File](./how-to-create-a-helpinfo-xml-file.md).</span></span>

### <a name="step-4-sign-your-help-files"></a><span data-ttu-id="99181-125">Schritt 4: Signieren der Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="99181-125">Step 4: Sign your help files</span></span>

<span data-ttu-id="99181-126">Digitale Signaturen sind nicht erforderlich, aber Sie sind eine bewährte Empfehlung, wenn Sie Dateien freigeben.</span><span class="sxs-lookup"><span data-stu-id="99181-126">Digital signatures are not required, but they are a best-practice recommendation whenever you are sharing files.</span></span>

### <a name="step-5-create-cab-files"></a><span data-ttu-id="99181-127">Schritt 5: Erstellen von CAB-Dateien</span><span class="sxs-lookup"><span data-stu-id="99181-127">Step 5: Create CAB files</span></span>

<span data-ttu-id="99181-128">Verwenden Sie ein Tool, mit dem CAB-Dateien (z. b. makecab. exe) erstellt werden, um eine zu erstellen. Die CAB-Datei, die die Hilfedateien für das Modul enthält.</span><span class="sxs-lookup"><span data-stu-id="99181-128">Use a tool that creates cabinet (.cab) files, such as MakeCab.exe, to create a .CAB file that contains the help files for your module.</span></span> <span data-ttu-id="99181-129">Erstellen Sie eine separate CAB-Datei für die Hilfedateien in jeder unterstützten Benutzeroberflächen Kultur.</span><span class="sxs-lookup"><span data-stu-id="99181-129">Create a separate CAB file for the help files in each supported UI culture.</span></span> <span data-ttu-id="99181-130">Weitere Informationen finden Sie unter [Vorbereiten der CAB-Dateien der aktualisierbaren Hilfe](./how-to-prepare-updatable-help-cab-files.md).</span><span class="sxs-lookup"><span data-stu-id="99181-130">For more information, see [How to Prepare Updatable Help CAB Files](./how-to-prepare-updatable-help-cab-files.md).</span></span>

### <a name="step-6-upload-your-files"></a><span data-ttu-id="99181-131">Schritt 6: Hochladen der Dateien</span><span class="sxs-lookup"><span data-stu-id="99181-131">Step 6: Upload your files</span></span>

<span data-ttu-id="99181-132">Zum Veröffentlichen neuer oder aktualisierter Hilfedateien laden Sie die CAB-Dateien an den Internet Speicherort hoch, der durch das **helpcontenturi** -Element in der helpinfo-XML-Datei angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="99181-132">To publish new or updated help files, upload the CAB files to the Internet location that is specified by the **HelpContentUri** element in the HelpInfo XML file.</span></span> <span data-ttu-id="99181-133">Laden Sie dann die helpinfo-XML-Datei an den Internet Speicherort hoch, der durch den Wert des **helpinfouri** -Schlüssels im Modul Manifest angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="99181-133">Then, upload the HelpInfo XML file to the Internet location that is specified by the value of the **HelpInfoUri** key in the module manifest.</span></span>

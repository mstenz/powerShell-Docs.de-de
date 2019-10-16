---
title: Vorgehensweise beim Hinzufügen einer Cmdlet-Beschreibung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361279"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="d226e-102">Hinzufügen einer Cmdlet-Beschreibung</span><span class="sxs-lookup"><span data-stu-id="d226e-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="d226e-103">In diesem Abschnitt wird beschrieben, wie Sie Inhalte hinzufügen, die im Abschnitt Beschreibung der Cmdlet-Hilfe angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="d226e-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="d226e-104">In der Hilfedatei wird dieser Inhalt dem Befehls Knoten für jedes Cmdlet hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d226e-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="d226e-105">Eine umfassende Übersicht über eine Hilfedatei erhalten Sie, indem Sie eine der dll-Help. XML-Dateien öffnen, die sich im Windows PowerShell-Installationsverzeichnis befinden.</span><span class="sxs-lookup"><span data-stu-id="d226e-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="d226e-106">Beispielsweise enthält die Datei Microsoft. PowerShell. Commands. Management. dll-Help. XML Inhalte für mehrere der Windows PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="d226e-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="d226e-107">So fügen Sie eine Beschreibung hinzu</span><span class="sxs-lookup"><span data-stu-id="d226e-107">To Add a Description</span></span>

- <span data-ttu-id="d226e-108">Erläutern Sie zunächst die grundlegenden Features des Cmdlets ausführlicher.</span><span class="sxs-lookup"><span data-stu-id="d226e-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="d226e-109">In vielen Fällen können Sie die im Cmdlet-Namen verwendeten Begriffe erläutern und unbekannte Konzepte mit einem Beispiel veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="d226e-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="d226e-110">Wenn das Cmdlet z. b. Daten an eine Datei anfügt, erklären Sie, dass die Daten am Ende einer vorhandenen Datei hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="d226e-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="d226e-111">Um alle Features des Cmdlets zu finden, überprüfen Sie die Parameterliste.</span><span class="sxs-lookup"><span data-stu-id="d226e-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="d226e-112">Beschreiben Sie die primäre Funktion des Cmdlets, und schließen Sie dann weitere Funktionen und Funktionen ein.</span><span class="sxs-lookup"><span data-stu-id="d226e-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="d226e-113">Wenn z. b. die Hauptfunktion des Cmdlets darin besteht, eine Eigenschaft zu ändern, das Cmdlet jedoch alle Eigenschaften ändern kann, sagen Sie dies in der detaillierten Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="d226e-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="d226e-114">Wenn die Cmdlet-Parameter den Benutzern die Möglichkeit geben, Informationen auf verschiedene Weise anzufordern, erklären Sie Sie.</span><span class="sxs-lookup"><span data-stu-id="d226e-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="d226e-115">Enthalten Informationen zu Möglichkeiten, mit denen Benutzer das Cmdlet zusätzlich zu den offensichtlichen Verwendungsmöglichkeiten verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d226e-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="d226e-116">Beispielsweise können Sie das-Objekt verwenden, das das `Get-Host`-Cmdlet abruft, um die Textfarbe im Windows PowerShell-Befehlsfenster zu ändern.</span><span class="sxs-lookup"><span data-stu-id="d226e-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="d226e-117">Beispiel: "das Cmdlet" `Get-Acl` "Ruft die Objekte ab, die die Sicherheits Beschreibung einer Datei oder Ressource darstellen.</span><span class="sxs-lookup"><span data-stu-id="d226e-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="d226e-118">Die Sicherheitsbeschreibung enthält die Zugriffssteuerungslisten (Access Control Lists, ACLs) der Ressource.</span><span class="sxs-lookup"><span data-stu-id="d226e-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="d226e-119">Die ACL gibt die Berechtigungen an, die Benutzer und Benutzergruppen für den Zugriff auf die Ressource haben.</span><span class="sxs-lookup"><span data-stu-id="d226e-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="d226e-120">Die ausführliche Beschreibung sollte das Cmdlet beschreiben, aber es sollte keine Konzepte beschreiben, die vom Cmdlet verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d226e-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="d226e-121">Legen Sie Konzept Definitionen in zusätzlichen Notizen ab.</span><span class="sxs-lookup"><span data-stu-id="d226e-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="d226e-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d226e-122">See Also</span></span>

[<span data-ttu-id="d226e-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d226e-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

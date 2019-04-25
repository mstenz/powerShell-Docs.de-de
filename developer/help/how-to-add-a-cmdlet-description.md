---
title: 'Gewusst wie: Hinzufügen einer Cmdlet-Beschreibung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083517"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="17244-102">Hinzufügen einer Cmdlet-Beschreibung</span><span class="sxs-lookup"><span data-stu-id="17244-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="17244-103">In diesem Abschnitt wird beschrieben, wie Inhalte hinzufügen, die in den Abschnitt "Beschreibung", der die Cmdlet-Hilfe angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="17244-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="17244-104">Dieser Inhalt wird in der Hilfedatei befehlsknoten für jedes Cmdlet hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="17244-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="17244-105">Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden.</span><span class="sxs-lookup"><span data-stu-id="17244-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="17244-106">Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="17244-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="17244-107">Eine Beschreibung hinzufügen</span><span class="sxs-lookup"><span data-stu-id="17244-107">To Add a Description</span></span>

- <span data-ttu-id="17244-108">Sie zunächst die grundlegenden Funktionen des-Cmdlets im Detail erläutert.</span><span class="sxs-lookup"><span data-stu-id="17244-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="17244-109">In vielen Fällen können Sie die in den Cmdlet-Namen verwendeten Begriffe erläutert und unbekannten Konzepte anhand eines Beispiels veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="17244-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="17244-110">Beispielsweise wenn Daten durch das Cmdlet in eine Datei angefügt wird, Erläutern Sie, dass es Daten an das Ende einer vorhandenen Datei hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="17244-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="17244-111">Um alle Features des-Cmdlets zu suchen, lesen Sie in der Parameterliste.</span><span class="sxs-lookup"><span data-stu-id="17244-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="17244-112">Beschreiben Sie die primäre Funktion des Cmdlets, und fügen Sie dann auf andere Funktionen und Features.</span><span class="sxs-lookup"><span data-stu-id="17244-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="17244-113">Wenn die Hauptfunktion des-Cmdlets, einer Eigenschaft zu ändern, aber das-Cmdlet kann alle Eigenschaften ändern, z. B. dies in der detaillierten Beschreibung.</span><span class="sxs-lookup"><span data-stu-id="17244-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="17244-114">Wenn Sie die Cmdlet-Parameter, die Benutzer auf unterschiedliche Weise Informationen anfordern können, erläutern.</span><span class="sxs-lookup"><span data-stu-id="17244-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="17244-115">Enthalten Sie Informationen zu Möglichkeiten, Benutzer zusätzlich zu den offensichtlichen verwendet das Cmdlet verwenden können.</span><span class="sxs-lookup"><span data-stu-id="17244-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="17244-116">Beispielsweise können Sie das Objekt, das die `Get-Host` Cmdlet abgerufen wird, um die Farbe des Texts in Windows PowerShell-Befehlsfenster zu ändern.</span><span class="sxs-lookup"><span data-stu-id="17244-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="17244-117">Beispiel:  "Die `Get-Acl` Cmdlet ruft Objekte, die die Sicherheitsbeschreibung für eine Datei oder Ressource darstellen.</span><span class="sxs-lookup"><span data-stu-id="17244-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="17244-118">Die Sicherheitsbeschreibung enthält die Zugriffssteuerungslisten (Access Control Lists, ACLs) der Ressource.</span><span class="sxs-lookup"><span data-stu-id="17244-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="17244-119">Die ACL gibt die Berechtigungen, die Benutzer und Benutzergruppen Zugriff auf die Ressource."</span><span class="sxs-lookup"><span data-stu-id="17244-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="17244-120">Die ausführliche Beschreibung sollte beschreiben, mit dem-Cmdlet, aber es sollte nicht beschreiben die Konzepte, die das Cmdlet verwendet.</span><span class="sxs-lookup"><span data-stu-id="17244-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="17244-121">Platzieren Sie Konzept Definitionen in zusätzlichen hinweisen.</span><span class="sxs-lookup"><span data-stu-id="17244-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="17244-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="17244-122">See Also</span></span>

[<span data-ttu-id="17244-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="17244-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

---
title: Windows PowerShell-Konzepten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: c4b13518ad6452a39ca49e897e1d3e353818d332
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081035"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="2cc6d-102">Windows PowerShell: Konzepte</span><span class="sxs-lookup"><span data-stu-id="2cc6d-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="2cc6d-103">Dieser Abschnitt enthält konzeptionelle Informationen, mit denen Sie die Windows PowerShell vom Standpunkt eines Entwicklers zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-103">This section contains conceptual information that will help you understand Windows PowerShell from the viewpoint of a developer.</span></span>

|<span data-ttu-id="2cc6d-104">Themenname</span><span class="sxs-lookup"><span data-stu-id="2cc6d-104">Topic Name</span></span>|<span data-ttu-id="2cc6d-105">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="2cc6d-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="2cc6d-106">Windows PowerShell-Anbieter</span><span class="sxs-lookup"><span data-stu-id="2cc6d-106">Windows PowerShell Providers</span></span>](http://msdn.microsoft.com/en-us/a65c5c75-1131-4ade-90d3-a613dbe620e9)|<span data-ttu-id="2cc6d-107">Eine Diskussion über Windows PowerShell-Anbieter, die verwendet werden, den Zugriff auf Daten speichert.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-107">A discussion about Windows PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="2cc6d-108">Windows PowerShell-Snap-ins</span><span class="sxs-lookup"><span data-stu-id="2cc6d-108">Windows PowerShell Snap-ins</span></span>](http://msdn.microsoft.com/en-us/20e081a9-522c-48bf-9f21-faaf8cca2e82)|<span data-ttu-id="2cc6d-109">Ein Mechanismus für die Registrierung der Cmdlets und Anbieter.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-109">A mechanism for registering cmdlets and providers.</span></span> <span data-ttu-id="2cc6d-110">(Siehe auch [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).)</span><span class="sxs-lookup"><span data-stu-id="2cc6d-110">(See also, [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).)</span></span>|
|[<span data-ttu-id="2cc6d-111">Windows PowerShell-Laufzeit</span><span class="sxs-lookup"><span data-stu-id="2cc6d-111">Windows PowerShell Runtime</span></span>](http://msdn.microsoft.com/en-us/949f06e8-0224-4cd3-bbad-a0cebbb5dec8)|<span data-ttu-id="2cc6d-112">Die aktuelle Instanz von der Windows PowerShell-Runspace.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-112">The current instance of the Windows PowerShell runspace.</span></span>|
|[<span data-ttu-id="2cc6d-113">Windows PowerShell-Runspaces</span><span class="sxs-lookup"><span data-stu-id="2cc6d-113">Windows PowerShell Runspaces</span></span>](http://msdn.microsoft.com/en-us/a1582cfe-f06d-4aff-adc6-71f49a860ce9)|<span data-ttu-id="2cc6d-114">Der betriebsumgebungen, in denen Befehle verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-114">The operating environments where commands are processed.</span></span>|
|[<span data-ttu-id="2cc6d-115">Windows PowerShell-Namespaces</span><span class="sxs-lookup"><span data-stu-id="2cc6d-115">Windows PowerShell Namespaces</span></span>](http://msdn.microsoft.com/en-us/04bd2841-e90c-47d2-8a1f-3aeb3df35176)|<span data-ttu-id="2cc6d-116">Übersicht über Windows PowerShell-API-Namespaces.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-116">Overview of Windows PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="2cc6d-117">Windows PowerShell-Hilfe</span><span class="sxs-lookup"><span data-stu-id="2cc6d-117">Windows PowerShell Help</span></span>](http://msdn.microsoft.com/en-us/097b7c1c-a056-4b36-9c86-65b2ee702fc7)|<span data-ttu-id="2cc6d-118">Eine Diskussion über das Schreiben von Cmdlet-Hilfe.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-118">A discussion about writing cmdlet Help.</span></span>|
|[<span data-ttu-id="2cc6d-119">Bestätigung anzufordern</span><span class="sxs-lookup"><span data-stu-id="2cc6d-119">Requesting Confirmation</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="2cc6d-120">Eine Diskussion darüber, wie Cmdlets und Anbieter aus dem Benutzer vor einer Aktion feedbackanforderung wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-120">A discussion about how cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="2cc6d-121">Konzepte von Windows PowerShell-Objekt</span><span class="sxs-lookup"><span data-stu-id="2cc6d-121">Windows PowerShell Object Concepts</span></span>](http://msdn.microsoft.com/en-us/a1449178-b6fd-4ca8-a5e1-d747c2c54181)|<span data-ttu-id="2cc6d-122">Behandlung von Windows PowerShell Objekte.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-122">How Windows PowerShell handles objects.</span></span>|
|[<span data-ttu-id="2cc6d-123">Windows PowerShell Extended Typensystem (ETS)</span><span class="sxs-lookup"><span data-stu-id="2cc6d-123">Windows PowerShell Extended Type System (ETS)</span></span>](http://msdn.microsoft.com/en-us/12700631-be23-4e6b-9bf0-81ea0d166353)|<span data-ttu-id="2cc6d-124">Programmgesteuertes Erweitern von Objekten.</span><span class="sxs-lookup"><span data-stu-id="2cc6d-124">Programmatically extending objects.</span></span>|

## <a name="see-also"></a><span data-ttu-id="2cc6d-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="2cc6d-125">See Also</span></span>

[<span data-ttu-id="2cc6d-126">Windows PowerShell Handbuch für Programmierer</span><span class="sxs-lookup"><span data-stu-id="2cc6d-126">Windows PowerShell Programmer's Guide</span></span>](./windows-powershell-programmer-s-guide.md)
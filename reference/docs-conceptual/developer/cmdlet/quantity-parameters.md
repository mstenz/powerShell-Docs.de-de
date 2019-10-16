---
title: Mengen Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369559"
---
# <a name="quantity-parameters"></a><span data-ttu-id="50e60-102">Mengenparameter</span><span class="sxs-lookup"><span data-stu-id="50e60-102">Quantity Parameters</span></span>

<span data-ttu-id="50e60-103">In der folgenden Tabelle werden die empfohlenen Namen und Funktionen für die Anzahl von Parametern aufgelistet.</span><span class="sxs-lookup"><span data-stu-id="50e60-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="50e60-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="50e60-104">Parameter</span></span>|<span data-ttu-id="50e60-105">Funktion</span><span class="sxs-lookup"><span data-stu-id="50e60-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="50e60-106">**Allen**</span><span class="sxs-lookup"><span data-stu-id="50e60-106">**All**</span></span><br><span data-ttu-id="50e60-107">Datentyp: Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="50e60-107">Data type: Boolean</span></span>|<span data-ttu-id="50e60-108">Implementieren Sie diesen Parameter, sodass `true` angibt, dass statt einer Standard Teilmenge von Ressourcen auf alle Ressourcen reagiert werden soll.</span><span class="sxs-lookup"><span data-stu-id="50e60-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="50e60-109">Implementieren Sie diesen Parameter, sodass `false` eine Teilmenge der Ressourcen angibt.</span><span class="sxs-lookup"><span data-stu-id="50e60-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="50e60-110">**Schichtung**</span><span class="sxs-lookup"><span data-stu-id="50e60-110">**Allocation**</span></span><br><span data-ttu-id="50e60-111">Datentyp: Int32</span><span class="sxs-lookup"><span data-stu-id="50e60-111">Data type: Int32</span></span>|<span data-ttu-id="50e60-112">Implementieren Sie diesen Parameter, sodass der Benutzer die Anzahl der zuzuordnenden Elemente angeben kann.</span><span class="sxs-lookup"><span data-stu-id="50e60-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="50e60-113">**Blockcount**</span><span class="sxs-lookup"><span data-stu-id="50e60-113">**BlockCount**</span></span><br><span data-ttu-id="50e60-114">Datentyp: Int64</span><span class="sxs-lookup"><span data-stu-id="50e60-114">Data type: Int64</span></span>|<span data-ttu-id="50e60-115">Implementieren Sie diesen Parameter, sodass der Benutzer die Anzahl der Blöcke angeben kann.</span><span class="sxs-lookup"><span data-stu-id="50e60-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="50e60-116">**Countdown**</span><span class="sxs-lookup"><span data-stu-id="50e60-116">**Count**</span></span><br><span data-ttu-id="50e60-117">Datentyp: Int64</span><span class="sxs-lookup"><span data-stu-id="50e60-117">Data type: Int64</span></span>|<span data-ttu-id="50e60-118">Implementieren Sie diesen Parameter, sodass der Benutzer die Anzahl angeben kann.</span><span class="sxs-lookup"><span data-stu-id="50e60-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="50e60-119">**Umfang**</span><span class="sxs-lookup"><span data-stu-id="50e60-119">**Scope**</span></span><br><span data-ttu-id="50e60-120">Datentyp: Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="50e60-120">Data type: Keyword</span></span>|<span data-ttu-id="50e60-121">Implementieren Sie diesen Parameter, sodass der Benutzer den Bereich angeben kann, der verarbeitet werden soll.</span><span class="sxs-lookup"><span data-stu-id="50e60-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="50e60-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="50e60-122">See Also</span></span>

[<span data-ttu-id="50e60-123">Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="50e60-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="50e60-124">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="50e60-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="50e60-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="50e60-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

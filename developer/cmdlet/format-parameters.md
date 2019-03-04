---
title: Formatieren von Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251182"
---
# <a name="format-parameters"></a><span data-ttu-id="3aac4-102">Formatparameter</span><span class="sxs-lookup"><span data-stu-id="3aac4-102">Format Parameters</span></span>

<span data-ttu-id="3aac4-103">Die folgende Tabelle enthält die empfohlenen Namen und Funktionen für Parameter, die zum Formatieren von oder zum Generieren von Daten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3aac4-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="3aac4-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="3aac4-104">Parameter</span></span>|<span data-ttu-id="3aac4-105">Funktion</span><span class="sxs-lookup"><span data-stu-id="3aac4-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="3aac4-106">**als**</span><span class="sxs-lookup"><span data-stu-id="3aac4-106">**As**</span></span><br><span data-ttu-id="3aac4-107">Datentyp: Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="3aac4-107">Data type: Keyword</span></span>|<span data-ttu-id="3aac4-108">Implementieren Sie diesen Parameter, um die Cmdlet-Ausgabeformat angeben.</span><span class="sxs-lookup"><span data-stu-id="3aac4-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="3aac4-109">Mögliche Werte möglicherweise z. B. Text oder ein Skript.</span><span class="sxs-lookup"><span data-stu-id="3aac4-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="3aac4-110">**Binary**</span><span class="sxs-lookup"><span data-stu-id="3aac4-110">**Binary**</span></span><br><span data-ttu-id="3aac4-111">Datentyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3aac4-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="3aac4-112">Implementieren Sie diesen Parameter, um anzugeben, dass das Cmdlet binäre Werte behandelt.</span><span class="sxs-lookup"><span data-stu-id="3aac4-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="3aac4-113">**Encoding**</span><span class="sxs-lookup"><span data-stu-id="3aac4-113">**Encoding**</span></span><br><span data-ttu-id="3aac4-114">Datentyp: Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="3aac4-114">Data type: Keyword</span></span>|<span data-ttu-id="3aac4-115">Implementieren Sie diesen Parameter, um den Typ der Codierung angeben, der unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="3aac4-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="3aac4-116">Mögliche Werte möglicherweise z. B. ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte und Zeichenfolge.</span><span class="sxs-lookup"><span data-stu-id="3aac4-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="3aac4-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="3aac4-117">**NewLine**</span></span><br><span data-ttu-id="3aac4-118">Datentyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3aac4-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="3aac4-119">Implementieren Sie diesen Parameter, sodass die neue Zeilenumbruchzeichen unterstützt werden, wenn der Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3aac4-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="3aac4-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="3aac4-120">**ShortName**</span></span><br><span data-ttu-id="3aac4-121">Datentyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3aac4-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="3aac4-122">Implementieren Sie diesen Parameter, sodass Kurznamen unterstützt werden, wenn der Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3aac4-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="3aac4-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="3aac4-123">**Width**</span></span><br><span data-ttu-id="3aac4-124">Datentyp: Int32</span><span class="sxs-lookup"><span data-stu-id="3aac4-124">Data type: Int32</span></span>|<span data-ttu-id="3aac4-125">Implementieren Sie diesen Parameter, damit der Benutzer die Breite des Ausgabegeräts angeben kann.</span><span class="sxs-lookup"><span data-stu-id="3aac4-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="3aac4-126">**wickeln**</span><span class="sxs-lookup"><span data-stu-id="3aac4-126">**Wrap**</span></span><br><span data-ttu-id="3aac4-127">Datentyp: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="3aac4-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="3aac4-128">Implementieren Sie diesen Parameter, sodass Umbrechen von Text unterstützt, wenn der Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="3aac4-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="3aac4-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3aac4-129">See Also</span></span>

[<span data-ttu-id="3aac4-130">Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="3aac4-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="3aac4-131">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="3aac4-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="3aac4-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="3aac4-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

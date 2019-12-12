---
title: Format Parameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369749"
---
# <a name="format-parameters"></a><span data-ttu-id="5841e-102">Formatparameter</span><span class="sxs-lookup"><span data-stu-id="5841e-102">Format Parameters</span></span>

<span data-ttu-id="5841e-103">In der folgenden Tabelle sind die empfohlenen Namen und Funktionen für Parameter aufgeführt, die zum Formatieren von oder zum Generieren von Daten verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="5841e-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="5841e-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="5841e-104">Parameter</span></span>|<span data-ttu-id="5841e-105">Funktion</span><span class="sxs-lookup"><span data-stu-id="5841e-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="5841e-106">**As**</span><span class="sxs-lookup"><span data-stu-id="5841e-106">**As**</span></span><br><span data-ttu-id="5841e-107">Datentyp: Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="5841e-107">Data type: Keyword</span></span>|<span data-ttu-id="5841e-108">Implementieren Sie diesen Parameter, um das Cmdlet-Ausgabeformat anzugeben.</span><span class="sxs-lookup"><span data-stu-id="5841e-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="5841e-109">Mögliche Werte sind z. b. Text oder Skripts.</span><span class="sxs-lookup"><span data-stu-id="5841e-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="5841e-110">**Binär (Binary)**</span><span class="sxs-lookup"><span data-stu-id="5841e-110">**Binary**</span></span><br><span data-ttu-id="5841e-111">Datentyp: Switchparameter</span><span class="sxs-lookup"><span data-stu-id="5841e-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="5841e-112">Implementieren Sie diesen Parameter, um anzugeben, dass das Cmdlet binäre Werte verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="5841e-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="5841e-113">**Codierung**</span><span class="sxs-lookup"><span data-stu-id="5841e-113">**Encoding**</span></span><br><span data-ttu-id="5841e-114">Datentyp: Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="5841e-114">Data type: Keyword</span></span>|<span data-ttu-id="5841e-115">Implementieren Sie diesen Parameter, um den Codierungstyp anzugeben, der unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="5841e-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="5841e-116">Mögliche Werte sind z. b. ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte und String.</span><span class="sxs-lookup"><span data-stu-id="5841e-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="5841e-117">**Zeilenumbruch**</span><span class="sxs-lookup"><span data-stu-id="5841e-117">**NewLine**</span></span><br><span data-ttu-id="5841e-118">Datentyp: Switchparameter</span><span class="sxs-lookup"><span data-stu-id="5841e-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="5841e-119">Implementieren Sie diesen Parameter, sodass die Zeilen Umleitungs Zeichen unterstützt werden, wenn der-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5841e-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="5841e-120">**Kurznamen**</span><span class="sxs-lookup"><span data-stu-id="5841e-120">**ShortName**</span></span><br><span data-ttu-id="5841e-121">Datentyp: Switchparameter</span><span class="sxs-lookup"><span data-stu-id="5841e-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="5841e-122">Implementieren Sie diesen Parameter, damit Kurznamen unterstützt werden, wenn der-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5841e-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="5841e-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="5841e-123">**Width**</span></span><br><span data-ttu-id="5841e-124">Datentyp: Int32</span><span class="sxs-lookup"><span data-stu-id="5841e-124">Data type: Int32</span></span>|<span data-ttu-id="5841e-125">Implementieren Sie diesen Parameter, sodass der Benutzer die Breite des Ausgabegeräts angeben kann.</span><span class="sxs-lookup"><span data-stu-id="5841e-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="5841e-126">**Anfield**</span><span class="sxs-lookup"><span data-stu-id="5841e-126">**Wrap**</span></span><br><span data-ttu-id="5841e-127">Datentyp: Switchparameter</span><span class="sxs-lookup"><span data-stu-id="5841e-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="5841e-128">Implementieren Sie diesen Parameter, sodass Text Wrapping unterstützt wird, wenn der-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="5841e-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="5841e-129">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5841e-129">See Also</span></span>

[<span data-ttu-id="5841e-130">Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="5841e-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="5841e-131">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="5841e-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="5841e-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="5841e-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)

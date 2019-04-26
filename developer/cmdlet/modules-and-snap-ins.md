---
title: Module und Snap-ins | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067619"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="b5d37-102">Module und Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="b5d37-102">Modules and Snap-ins</span></span>

<span data-ttu-id="b5d37-103">Cmdlets können per (von Windows PowerShell 2.0 eingeführt) Module oder Snap-ins zu einer Sitzung hinzugefügt werden. Sobald das-Cmdlet mit der Sitzung hinzugefügt wird, die sie programmgesteuert von einer hostanwendung oder interaktiv in der Befehlszeile ausgeführt werden kann.</span><span class="sxs-lookup"><span data-stu-id="b5d37-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="b5d37-104">Es wird empfohlen, als die Übermittlungsmethode für das Hinzufügen von Cmdlets zu einer Sitzung den folgenden Gründen Module zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="b5d37-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="b5d37-105">Module können Cmdlets hinzufügen, indem Sie das Laden der Assembly, in dem das Cmdlet definiert ist.</span><span class="sxs-lookup"><span data-stu-id="b5d37-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="b5d37-106">Es ist nicht erforderlich, eine Snap-in-Klasse zu implementieren.</span><span class="sxs-lookup"><span data-stu-id="b5d37-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="b5d37-107">Module können Sie andere Ressourcen, z. B. Variablen, Funktionen, Skripts, Typen und Formatierung Dateien und mehr hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b5d37-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="b5d37-108">-Snap-ins kann verwendet werden, nur für Cmdlets und Anbieter zur Sitzung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b5d37-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5d37-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b5d37-109">See Also</span></span>

[<span data-ttu-id="b5d37-110">Schreiben eines Windows PowerShell-Moduls</span><span class="sxs-lookup"><span data-stu-id="b5d37-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="b5d37-111">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b5d37-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

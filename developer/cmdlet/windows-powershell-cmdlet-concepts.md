---
title: Windows PowerShell-Cmdlet-Konzepte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067068"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="908da-102">Konzepte von Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="908da-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="908da-103">In diesem Abschnitt wird beschrieben, wie Cmdlets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="908da-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="908da-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="908da-104">In This Section</span></span>

<span data-ttu-id="908da-105">In diesem Abschnitt werden folgende Themen behandelt.</span><span class="sxs-lookup"><span data-stu-id="908da-105">This section includes the following topics.</span></span>

<span data-ttu-id="908da-106">[Richtlinien für die Entwicklung von Cmdlets](./cmdlet-development-guidelines.md) dieses Thema enthält Richtlinien für die Entwicklung, die verwendet werden können, um wohlgeformte-Cmdlets zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="908da-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="908da-107">[Cmdlet-Klassendeklaration](./cmdlet-class-declaration.md) in diesem Thema wird beschrieben, die Deklaration der Cmdlet-Klasse.</span><span class="sxs-lookup"><span data-stu-id="908da-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="908da-108">[Genehmigte Verben für Windows PowerShell-Befehle](./approved-verbs-for-windows-powershell-commands.md) in diesem Thema listet die vordefinierten Cmdlet-Verben, die Sie verwenden können, wenn Sie eine Cmdlet-Klasse deklarieren.</span><span class="sxs-lookup"><span data-stu-id="908da-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="908da-109">[-Cmdlet verarbeitet Eingabemethoden](./cmdlet-input-processing-methods.md) in diesem Thema wird beschrieben, die Methoden, mit denen ein Cmdlet zum vorverarbeitung Vorgänge ausführen, Eingabe verarbeiten von Vorgängen und Verarbeitungsvorgängen zu Posten.</span><span class="sxs-lookup"><span data-stu-id="908da-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="908da-110">[Cmdlet-Parameter](./cmdlet-parameters.md) in diesem Abschnitt wird beschrieben, die verschiedenen Arten von Parametern, die Sie für Cmdlets hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="908da-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="908da-111">[Cmdlet-Attribute](./cmdlet-attributes.md) in diesem Abschnitt wird beschrieben, die Attribute, die verwendet werden, um .NET Framework-Klassen wie Cmdlets, zu deklarieren, um Felder als Cmdlet-Parameter deklariert und Überprüfung der Eingabe-Regeln für den Parameter zu deklarieren.</span><span class="sxs-lookup"><span data-stu-id="908da-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="908da-112">[Cmdlet-Aliase](./cmdlet-aliases.md) in diesem Thema wird beschrieben, Cmdlet-Aliase.</span><span class="sxs-lookup"><span data-stu-id="908da-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="908da-113">[Cmdlet-Ausgabe](./cmdlet-output.md) in diesem Abschnitt wird beschrieben, den Typ der Ausgabe, die Cmdlets zurückgeben können und wie Sie definieren, und zeigt die Objekte, die mithilfe von Cmdlets zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="908da-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="908da-114">[Registrierung der Cmdlets](./modules-and-snap-ins.md) in diesem Abschnitt wird beschrieben, wie Sie Cmdlets, die mithilfe von Module und Snap-ins registrieren.</span><span class="sxs-lookup"><span data-stu-id="908da-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="908da-115">[Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md) in diesem Abschnitt wird beschrieben, wie Cmdlets Bestätigung der Anfrage von einem Benutzer, bevor sie eine Änderung am System vornehmen.</span><span class="sxs-lookup"><span data-stu-id="908da-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="908da-116">[Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md) in diesem Abschnitt wird beschrieben, wie Cmdlets Fehler mit Abbruch und Fehler ohne Abbruch gemeldet werden, und es wird beschrieben, wie zum Interpretieren von fehlerdatensätzen.</span><span class="sxs-lookup"><span data-stu-id="908da-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="908da-117">[Hintergrundaufträge](./background-jobs.md) in diesem Thema wird beschrieben, wie Cmdlets ihre Arbeit innerhalb Hintergrundaufträge ausführen können, die nicht mit den Befehlen beeinträchtigen, die in der aktuellen Sitzung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="908da-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="908da-118">[Aufrufen von Cmdlets und Skripts in ein Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) diesem Thema wird beschrieben, wie Cmdlets andere Cmdlets und Skripts innerhalb ihrer eingabeverarbeitungsmethoden aufrufen kann.</span><span class="sxs-lookup"><span data-stu-id="908da-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="908da-119">[-Cmdlet wird](./cmdlet-sets.md) dieses Thema beschreibt die Verwendung von Basisklassen Sätze von Cmdlets zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="908da-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="908da-120">[Windows PowerShell-Sitzungsstatus](./windows-powershell-session-state.md) dieses Thema beschreibt den Status der Windows PowerShell-Sitzung.</span><span class="sxs-lookup"><span data-stu-id="908da-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>

---
title: Konzepte von Windows PowerShell-Cmdlets | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b3ef3f4-c626-4679-884f-406a37412b3e
caps.latest.revision: 16
ms.openlocfilehash: 2f84c57da7429462c69b2a020d9f8ac04f8d0f35
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369119"
---
# <a name="windows-powershell-cmdlet-concepts"></a><span data-ttu-id="8fabe-102">Konzepte von Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8fabe-102">Windows PowerShell Cmdlet Concepts</span></span>

<span data-ttu-id="8fabe-103">In diesem Abschnitt wird beschrieben, wie Cmdlets funktionieren.</span><span class="sxs-lookup"><span data-stu-id="8fabe-103">This section describes how cmdlets work.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="8fabe-104">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="8fabe-104">In This Section</span></span>

<span data-ttu-id="8fabe-105">In diesem Abschnitt werden folgende Themen behandelt.</span><span class="sxs-lookup"><span data-stu-id="8fabe-105">This section includes the following topics.</span></span>

<span data-ttu-id="8fabe-106">[Cmdlet-Entwicklungs Richtlinien](./cmdlet-development-guidelines.md) Dieses Thema enthält Entwicklungs Richtlinien, die zum Entwickeln von wohlgeformten Cmdlets verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="8fabe-106">[Cmdlet Development Guidelines](./cmdlet-development-guidelines.md) This topic provides development guidelines that can be used to produce well-formed cmdlets.</span></span>

<span data-ttu-id="8fabe-107">[Cmdlet-Klassen Deklaration](./cmdlet-class-declaration.md) In diesem Thema wird die Cmdlet-Klassen Deklaration beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8fabe-107">[Cmdlet Class Declaration](./cmdlet-class-declaration.md) This topic describes cmdlet class declaration.</span></span>

<span data-ttu-id="8fabe-108">[Genehmigte Verben für Windows PowerShell-Befehle](./approved-verbs-for-windows-powershell-commands.md) In diesem Thema werden die vordefinierten Cmdlet-Verben aufgelistet, die Sie verwenden können, wenn Sie eine Cmdlet-Klasse deklarieren.</span><span class="sxs-lookup"><span data-stu-id="8fabe-108">[Approved Verbs for Windows PowerShell Commands](./approved-verbs-for-windows-powershell-commands.md) This topic lists the predefined cmdlet verbs that you can use when you declare a cmdlet class.</span></span>

<span data-ttu-id="8fabe-109">[Cmdlet-Eingabe Verarbeitungsmethoden](./cmdlet-input-processing-methods.md) In diesem Thema werden die Methoden beschrieben, mit denen ein Cmdlet Vorverarbeitungs Vorgänge, Eingabe Verarbeitungsvorgänge und nach Verarbeitungsvorgänge ausführen kann.</span><span class="sxs-lookup"><span data-stu-id="8fabe-109">[Cmdlet Input Processing Methods](./cmdlet-input-processing-methods.md) This topic describes the methods that allow a cmdlet to perform preprocessing operations, input processing operations, and post processing operations.</span></span>

<span data-ttu-id="8fabe-110">[Cmdlet-Parameter](./cmdlet-parameters.md) In diesem Abschnitt werden die verschiedenen Parametertypen beschrieben, die Sie Cmdlets hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="8fabe-110">[Cmdlet Parameters](./cmdlet-parameters.md) This section describes the different types of parameters that you can add to cmdlets.</span></span>

<span data-ttu-id="8fabe-111">[Cmdlet-Attribute](./cmdlet-attributes.md) In diesem Abschnitt werden die Attribute beschrieben, die zum Deklarieren von .NET Framework Klassen als Cmdlets, zum Deklarieren von Feldern als Cmdlet-Parameter und zum Deklarieren von Eingabe Validierungsregeln für Parameter verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8fabe-111">[Cmdlet Attributes](./cmdlet-attributes.md) This section describes the attributes that are used to declare .NET Framework classes as cmdlets, to declare fields as cmdlet parameters, and to declare input validation rules for parameters.</span></span>

<span data-ttu-id="8fabe-112">[Cmdlet-Aliase](./cmdlet-aliases.md) In diesem Thema werden Cmdlet-Aliase beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8fabe-112">[Cmdlet Aliases](./cmdlet-aliases.md) This topic describes cmdlet aliases.</span></span>

<span data-ttu-id="8fabe-113">[Cmdlet-Ausgabe](./cmdlet-output.md) In diesem Abschnitt wird der Typ der Ausgabe beschrieben, die von Cmdlets zurückgegeben werden können, und das definieren und Anzeigen der Objekte, die von Cmdlets zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8fabe-113">[Cmdlet Output](./cmdlet-output.md) This section describes the type of output that cmdlets can return and how to define and display the objects that are returned by cmdlets.</span></span>

<span data-ttu-id="8fabe-114">[Cmdlets werden registriert](./modules-and-snap-ins.md) In diesem Abschnitt wird beschrieben, wie Cmdlets mithilfe von Modulen und Snap-Ins registriert werden.</span><span class="sxs-lookup"><span data-stu-id="8fabe-114">[Registering Cmdlets](./modules-and-snap-ins.md) This section describes how to register cmdlets by using modules and snap-ins.</span></span>

<span data-ttu-id="8fabe-115">[Anfordern der Bestätigung](./requesting-confirmation-from-cmdlets.md) In diesem Abschnitt wird beschrieben, wie Cmdlets die Bestätigung eines Benutzers anfordern, bevor Sie eine Änderung am System vornehmen.</span><span class="sxs-lookup"><span data-stu-id="8fabe-115">[Requesting Confirmation](./requesting-confirmation-from-cmdlets.md) This section describes how cmdlets request confirmation from a user before they make a change to the system.</span></span>

<span data-ttu-id="8fabe-116">[Windows PowerShell-Fehlerberichterstattung](./error-reporting-concepts.md) In diesem Abschnitt wird beschrieben, wie die Fehler Datensätze von Cmdlets abgebrochen werden, und es wird beschrieben, wie Fehler Datensätze interpretiert werden.</span><span class="sxs-lookup"><span data-stu-id="8fabe-116">[Windows PowerShell Error Reporting](./error-reporting-concepts.md) This section describes how cmdlets report terminating errors and non-terminating errors, and it describes how to interpret error records.</span></span>

<span data-ttu-id="8fabe-117">[Hintergrund Aufträge](./background-jobs.md) In diesem Thema wird beschrieben, wie Cmdlets ihre Arbeit innerhalb von Hintergrund Aufträgen ausführen können, die nicht die Befehle beeinträchtigen, die in der aktuellen Sitzung ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="8fabe-117">[Background Jobs](./background-jobs.md) This topic describes how cmdlets can perform their work within background jobs that do not interfere with the commands that are executing in the current session.</span></span>

<span data-ttu-id="8fabe-118">[Aufrufen von Cmdlets und Skripts in einem Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) In diesem Thema wird beschrieben, wie Cmdlets andere Cmdlets und Skripts innerhalb Ihrer Eingabe Verarbeitungsmethoden aufrufen können.</span><span class="sxs-lookup"><span data-stu-id="8fabe-118">[Invoking Cmdlets and Scripts Within a Cmdlet](./invoking-cmdlets-and-scripts-within-a-cmdlet.md) This topic describes how cmdlets can invoke other cmdlets and scripts from within their input processing methods.</span></span>

<span data-ttu-id="8fabe-119">[Cmdlet-Sätze](./cmdlet-sets.md) In diesem Thema wird beschrieben, wie Sie mithilfe von Basisklassen Cmdlets erstellen.</span><span class="sxs-lookup"><span data-stu-id="8fabe-119">[Cmdlet Sets](./cmdlet-sets.md) This topic describes using base classes to create sets of cmdlets.</span></span>

<span data-ttu-id="8fabe-120">[Windows PowerShell-Sitzungs Status](./windows-powershell-session-state.md) In diesem Thema wird der Windows PowerShell-Sitzungszustand beschrieben.</span><span class="sxs-lookup"><span data-stu-id="8fabe-120">[Windows PowerShell Session State](./windows-powershell-session-state.md) This topic describes Windows PowerShell session state.</span></span>

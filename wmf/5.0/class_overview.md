---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: dfc171f9a3471f8fe7801283dd4a9b06860781a2
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225724"
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="5a7f2-102">Erstellen benutzerdefinierter Typen mithilfe von PowerShell-Klassen</span><span class="sxs-lookup"><span data-stu-id="5a7f2-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="5a7f2-103">Wir haben die PowerShell-Sprache zum Definieren von Klassen und anderen benutzerdefinierten Typen mithilfe formaler Syntax und Semantik verbessert, die mit anderen objektorientierten Programmiersprachen vergleichbar sind.</span><span class="sxs-lookup"><span data-stu-id="5a7f2-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="5a7f2-104">Ziel ist es, Entwickler und IT-Experten zu ermöglichen, PowerShell für eine größere Anzahl von Anwendungsfällen zu nutzen, die Entwicklung von PowerShell-Elementen (z. B. DSC-Ressourcen) zu vereinfachen und die Abdeckung weiterer Verwaltungsschnittstellen zu beschleunigen.</span><span class="sxs-lookup"><span data-stu-id="5a7f2-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="5a7f2-105">In dieser Version unterstützte Szenarien</span><span class="sxs-lookup"><span data-stu-id="5a7f2-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="5a7f2-106">Definieren von DSC-Ressourcen und ihren zugehörigen Typen mithilfe der PowerShell-Sprache</span><span class="sxs-lookup"><span data-stu-id="5a7f2-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="5a7f2-107">Definieren benutzerdefinierter Typen in PowerShell mithilfe vertrauter objektorientierter Programmierkonstrukte, z. B. Klassen, Eigenschaften, Methoden usw.</span><span class="sxs-lookup"><span data-stu-id="5a7f2-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="5a7f2-108">Unterstützung der Vererbung von Klassen in PowerShell und Basisklassen für DSC-Ressourcen</span><span class="sxs-lookup"><span data-stu-id="5a7f2-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="5a7f2-109">Debuggen von Typen mithilfe der PowerShell-Sprache</span><span class="sxs-lookup"><span data-stu-id="5a7f2-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="5a7f2-110">Generieren und Behandeln von Ausnahmen mithilfe formaler Mechanismen auf der richtigen Ebene</span><span class="sxs-lookup"><span data-stu-id="5a7f2-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>

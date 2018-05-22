---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 3f73b7cf0cdf033cbd561b3412734692bb7decd7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
---
# <a name="allowing-for-identical-duplicate-resources-in-a-configuration"></a><span data-ttu-id="9719a-102">Zulassen identischer doppelter Ressourcen in einer Konfiguration</span><span class="sxs-lookup"><span data-stu-id="9719a-102">Allowing for Identical Duplicate Resources in a Configuration</span></span>

<span data-ttu-id="9719a-103">DSC lässt keine in Konflikt stehenden Ressourcendefinitionen in einer Konfiguration zu bzw. behandeln diese nicht.</span><span class="sxs-lookup"><span data-stu-id="9719a-103">DSC does not allow or handle conflicting resource definitions within a configuration.</span></span> <span data-ttu-id="9719a-104">Anstatt zu versuchen, den Konflikt zu lösen, tritt ein Fehler auf.</span><span class="sxs-lookup"><span data-stu-id="9719a-104">Instead of trying to resolve the conflict, it simply fails.</span></span> <span data-ttu-id="9719a-105">Sobald die Wiederverwendung von Konfigurationen mittels zusammengesetzter Ressourcen häufiger vorkommt, werden Konflikte häufiger auftreten.</span><span class="sxs-lookup"><span data-stu-id="9719a-105">As configuration reuse becomes more utilized through composite resources, etc. conflicts will occur more often.</span></span> <span data-ttu-id="9719a-106">Wenn in Konflikt stehende Ressourcendefinitionen identisch sind, sollte DSC diese intelligent zulassen.</span><span class="sxs-lookup"><span data-stu-id="9719a-106">When conflicting resource definitions are identical, DSC should be smart and allow this.</span></span> <span data-ttu-id="9719a-107">In dieser Version unterstützen wir mehrere Ressourceninstanzen, die identische Definitionen aufweisen:</span><span class="sxs-lookup"><span data-stu-id="9719a-107">With this release, we support having multiple resource instances that have identical definitions:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS         #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS      #Identical resource
    {
        Ensure = 'Present'
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="9719a-108">In früheren Versionen wäre das Ergebnis eine fehlerhafte Kompilierung aufgrund eines Konflikts zwischen der „WindowsFeature FE_IIS“-Instanz und der „WindowsFeature Worker_IIS“-Instanz beim Versuch sicherzustellen, dass die Roll „Web-Server“ installiert ist.</span><span class="sxs-lookup"><span data-stu-id="9719a-108">In previous releases, the result would be a failed compilation due to a conflict between the WindowsFeature FE_IIS and WindowsFeature Worker_IIS instances trying to ensure the 'Web-Server' role is installed.</span></span> <span data-ttu-id="9719a-109">Beachten Sie, dass *alle* Eigenschaften, die konfiguriert werden, in diesen beiden Konfigurationen identisch sind.</span><span class="sxs-lookup"><span data-stu-id="9719a-109">Notice that *all* of the properties that are being configured are identical in these two configurations.</span></span> <span data-ttu-id="9719a-110">Da *alle* Eigenschaften in diesen beiden Ressourcen identisch sind, führt dies jetzt zu einer erfolgreichen Kompilierung.</span><span class="sxs-lookup"><span data-stu-id="9719a-110">Since *all* of the properties in these two resources are identical, this will result in a successful compilation now.</span></span>

<span data-ttu-id="9719a-111">Wenn Eigenschaften in beiden Ressourcen unterschiedlich sind, werden sie nicht als identisch eingestuft, weshalb die Kompilierung misslingt:</span><span class="sxs-lookup"><span data-stu-id="9719a-111">If any of the properties are different between the two resources, they will not be considered identical and compilation will fail:</span></span>

```powershell
Configuration IIS_FrontEnd
{
    WindowsFeature FE_IIS
    {
        Ensure = 'Present'     # Ensure is Present here
        Name = 'Web-Server'
    }

    WindowsFeature FTP
    {
        Ensure = 'Present'
        Name = 'Web-FTP-Server'
    }
}

Configuration IIS_Worker
{
    WindowsFeature Worker_IIS
    {
        Ensure = 'Absent'      # Ensure property is Absent instead of Present
        Name = 'Web-Server'
    }

    WindowsFeature ASP
    {
        Ensure = 'Present'
        Name = 'Web-ASP-Net45'
    }
}

Configuration WebApplication
{
    IIS_Frontend Web {}

    IIS_Worker ASP {}
}
```

<span data-ttu-id="9719a-112">Diese sehr ähnliche Konfiguration ist nicht erfolgreich, da die Ressourcen „WindowsFeature FE_IIS“ und „WindowsFeature Worker_IIS“ nicht mehr identisch sind und daher in Konflikt stehen.</span><span class="sxs-lookup"><span data-stu-id="9719a-112">This very similar configuration will fail because the WindowsFeature FE_IIS and the WindowsFeature Worker_IIS resources are no longer identical and therefore conflict.</span></span>

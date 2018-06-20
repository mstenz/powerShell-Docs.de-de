---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 0543afbc72148b1ba713e59655126c069b16ef33
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218432"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für DSC-Ressourcen

Module unterschiedlicher Versionen mit DSC-Ressourcen können parallel installiert werden, und DSC-Konfigurationen können eine bestimmte Version der Ressource verwenden, die auf dem System installiert ist.

Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Bekannte Probleme

In dieser Version sind die folgenden Probleme bei paralleler Installation unterschiedlicher Versionen bekannt:

-   Das Verwenden zweier verschiedener Versionen der DSC-Ressourcen innerhalb der gleichen Konfiguration wird nicht unterstützt.

---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b31fe833fb0f9d0f3f2733e777e4608a697d583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057926"
---
# <a name="side-by-side-module-versioning-support-for-dsc-resources"></a>Unterstützung der gleichzeitigen Ausführung unterschiedlicher Versionen für DSC-Ressourcen

Module unterschiedlicher Versionen mit DSC-Ressourcen können parallel installiert werden, und DSC-Konfigurationen können eine bestimmte Version der Ressource verwenden, die auf dem System installiert ist.

Weitere Informationen finden Sie unter [Verwenden von Ressourcen mit mehreren Versionen](https://msdn.microsoft.com/powershell/dsc/sxsresource).

## <a name="known-issues"></a>Bekannte Probleme

In dieser Version sind die folgenden Probleme bei paralleler Installation unterschiedlicher Versionen bekannt:

-   Das Verwenden zweier verschiedener Versionen der DSC-Ressourcen innerhalb der gleichen Konfiguration wird nicht unterstützt.

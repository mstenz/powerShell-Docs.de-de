---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 42f323590609319388e9a0a2c7c305dfa80c2d49
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="class-based-dsc-resources"></a>Klassenbasierte DSC-Ressourcen

## <a name="defining-dsc-resources-with-classes"></a>Definieren von DSC-Ressourcen mit Klassen

Basierend auf Feedback haben wir das Erstellen klassenbasierter DSC-Ressourcen vereinfacht und leichter verständlich gemacht.
Es folgen die wichtigsten Unterschiede zwischen einer klassenbasierten DSC-Ressource und einem DSC-Ressourcenanbieter für ein Cmdlet:

* Eine MOF-Datei für das Schema ist nicht erforderlich.
* Der Unterordner **DSCResource** im Ordner „module“ ist nicht erforderlich.
* Eine PowerShell-Moduldatei kann mehrere DSC-Ressourcenklassen enthalten.

Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).

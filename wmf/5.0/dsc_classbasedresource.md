---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: a1e90a0b96f74decb55343292b97befaf1a85f8a
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058113"
---
# <a name="class-based-dsc-resources"></a>Klassenbasierte DSC-Ressourcen

## <a name="defining-dsc-resources-with-classes"></a>Definieren von DSC-Ressourcen mit Klassen

Basierend auf Feedback haben wir das Erstellen klassenbasierter DSC-Ressourcen vereinfacht und leichter verständlich gemacht.
Es folgen die wichtigsten Unterschiede zwischen einer klassenbasierten DSC-Ressource und einem DSC-Ressourcenanbieter für ein Cmdlet:

* Eine MOF-Datei für das Schema ist nicht erforderlich.
* Der Unterordner **DSCResource** im Ordner „module“ ist nicht erforderlich.
* Eine PowerShell-Moduldatei kann mehrere DSC-Ressourcenklassen enthalten.

Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).

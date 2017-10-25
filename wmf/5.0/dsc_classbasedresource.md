---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: d40e5475c4132d6377c9a4559262a41b4842180a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="class-based-dsc-resources"></a>Klassenbasierte DSC-Ressourcen

## <a name="defining-dsc-resources-with-classes"></a>Definieren von DSC-Ressourcen mit Klassen

Basierend auf Feedback haben wir das Erstellen klassenbasierter DSC-Ressourcen vereinfacht und leichter verständlich gemacht. Es folgen die wichtigsten Unterschiede zwischen einer klassenbasierten DSC-Ressource und einem DSC-Ressourcenanbieter für ein Cmdlet:

* Eine MOF-Datei für das Schema ist nicht erforderlich.
* Der Unterordner **DSCResource** im Ordner „module“ ist nicht erforderlich.
* Eine PowerShell-Moduldatei kann mehrere DSC-Ressourcenklassen enthalten.

Weitere Informationen finden Sie unter [Schreiben einer benutzerdefinierten DSC-Ressource mit PowerShell-Klassen](https://msdn.microsoft.com/powershell/dsc/authoringresource).


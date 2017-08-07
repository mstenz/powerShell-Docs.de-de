---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Objektpipeline
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 3fa41cc744cf3ab66fc5ef186ead8eb919429a76
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="object-pipeline"></a>Objektpipeline
Eine Pipeline fungiert als eine Reihe von verbundenen Segmenten eines Rohrs. Elemente, die durch die Pipeline geleitet werden, durchlaufen jedes Segment. Um eine Pipeline in Windows PowerShell zu erstellen, verbinden Sie Befehle mit dem Pipeoperator „|“. Die Ausgabe eines Befehls wird als Eingabe des nächsten Befehls verwendet.

Pipelines sind wohl das wertvollste Konzept, das Befehlszeilenschnittstellen verwendet wird. Bei korrekter Verwendung verringern Pipelines nicht nur den Aufwand, der zum Eingeben komplexer Befehle erforderlich ist, sondern lassen auch einfacher erkennen, wie der Arbeitsablauf in den Befehlen aussieht. Weil in Pipelines jedes Element einzeln verarbeitet wird, haben sie die zugehörige nützliche Eigenschaft, dass Sie eine Pipeline nicht abhängig davon ändern müssen, wie viele Elemente es in ihr gibt. Darüber hinaus übergibt jeder Befehl in einer Pipeline (als Pipelineelement bezeichnet) üblicherweise seine Ausgabe elementweise an den nächsten Befehl in der Pipeline. Dadurch wird normalerweise der Ressourcenbedarf von komplexen Befehle verringert und wird es Ihnen ermöglicht, sofort mit dem Abrufen der Ausgabe zu beginnen.

In diesem Kapitel wird beschrieben, wie sich die Windows PowerShell-Pipeline von den Pipelines der meisten bekannten Shells unterscheidet, und anschließend werden einige grundlegende Tools veranschaulicht, mit denen Sie die Ausgabe einer Pipeline steuern sowie sehen können, wie die jeweilige Pipeline funktioniert.


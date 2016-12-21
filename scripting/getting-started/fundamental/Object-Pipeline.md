---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Objektpipeline
ms.technology: powershell
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 531c3c00ddcc0cc8299875392832fb1dad9f49d8
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="object-pipeline"></a>Objektpipeline
Eine Pipeline fungiert als eine Reihe von verbundenen Segmenten eines Rohrs. Elemente, die durch die Pipeline geleitet werden, durchlaufen jedes Segment. Um eine Pipeline in Windows PowerShell zu erstellen, verbinden Sie Befehle mit dem Pipeoperator „|“. Die Ausgabe eines Befehls wird als Eingabe des nächsten Befehls verwendet.

Pipelines sind wohl das wertvollste Konzept, das Befehlszeilenschnittstellen verwendet wird. Bei korrekter Verwendung verringern Pipelines nicht nur den Aufwand, der zum Eingeben komplexer Befehle erforderlich ist, sondern lassen auch einfacher erkennen, wie der Arbeitsablauf in den Befehlen aussieht. Weil in Pipelines jedes Element einzeln verarbeitet wird, haben sie die zugehörige nützliche Eigenschaft, dass Sie eine Pipeline nicht abhängig davon ändern müssen, wie viele Elemente es in ihr gibt. Darüber hinaus übergibt jeder Befehl in einer Pipeline (als Pipelineelement bezeichnet) üblicherweise seine Ausgabe elementweise an den nächsten Befehl in der Pipeline. Dadurch wird normalerweise der Ressourcenbedarf von komplexen Befehle verringert und wird es Ihnen ermöglicht, sofort mit dem Abrufen der Ausgabe zu beginnen.

In diesem Kapitel wird beschrieben, wie sich die Windows PowerShell-Pipeline von den Pipelines der meisten bekannten Shells unterscheidet, und anschließend werden einige grundlegende Tools veranschaulicht, mit denen Sie die Ausgabe einer Pipeline steuern sowie sehen können, wie die jeweilige Pipeline funktioniert.


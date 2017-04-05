---
title: "Windows PowerShell DSC – Übersicht"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: ec773688540a3f4a2f128f66d311926fd5b9a935
ms.sourcegitcommit: 6d27d6db5ab0e2d5b6c7229e2e2d2e57915ea22d
translationtype: HT
---
# <a name="windows-powershell-desired-state-configuration-overview"></a>Windows PowerShell DSC – Übersicht 

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

DSC ist eine Verwaltungsplattform in PowerShell, die es Ihnen ermöglicht, Ihre IT- und Entwicklungsinfrastruktur mit der Konfiguration als Code zu verwalten.

- Eine Übersicht über Vorteile, die DSC Ihrem Unternehmen bietet, finden Sie unter [Desired State Configuration (DSC): Übersicht für Entscheidungsträger](decisionMaker.md).
- Eine Übersicht über die Vorteile, die DSC Ihren Ingenieuren bietet, finden Sie unter [Desired State Configuration (DSC): Übersicht für Ingenieure](DscForEngineers.md).
- Informationen zum Schnelleinstieg in DSC finden Sie unter [DSC Schnellstart](quickStart.md).

## <a name="key-concepts"></a>Wichtige Konzepte

DSC ist eine deklarative Plattform für die Konfiguration, Bereitstellung und Verwaltung von Systemen, die aus drei Hauptkomponenten besteht:

- [Konfigurationen](configurations.md) sind deklarative PowerShell-Skripts, mit denen Instanzen von Ressourcen definiert und konfiguriert werden.
    Bei Ausführung der Konfiguration wird der gewünschte Zustand entsprechend den Vorgaben in der Konfiguration von DSC eingerichtet. 
    DSC-Konfigurationen sind auch idempotent, d. h. vom lokalen Konfigurations-Manager (LCM) wird weiter sicherstellt, dass Computer entsprechend der Deklaration in der Konfiguration konfiguriert werden.
- Ressourcen sind der „Mach es so“-Teil von DSC. Sie enthalten den Code, der das Ziel einer Konfiguration in den angegebenen Zustand versetzt und dort hält. 
    Ressourcen befinden sich in PowerShell-Modulen und können geschrieben werden, um etwas Allgemeines wie eine Datei oder einen Windows-Prozess oder etwas Spezifisches wie einen IIS-Server oder eine in Azure ausgeführte VM zu modellieren.
- Der lokale Konfigurations-Manager (Local Configuration Manager, LCM) ist das Modul, dass DSC die Interaktion zwischen Ressourcen und Konfigurationen erleichtert. 
    Der LCM fragt das System mithilfe der von Ressourcen implementierten Ablaufsteuerung ab, um sicherzustellen, dass der von einer Konfiguration definierte Zustand beibehalten wird. 
    Ist dies nicht der Fall, führt der LCM Aufrufe an Code in den Ressourcen aus, um eine Korrektur entsprechend der Konfiguration vorzunehmen. 

## <a name="see-also"></a>Weitere Informationen

- [DSC-Konfigurationen](configurations.md)
- [DSC-Ressourcen](resources.md)
- [Konfigurieren des lokalen Konfigurations-Managers](metaConfig.md)


---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: "Logik zum Vorbereiten der Modulabhängigkeiten während des Veröffentlichungsvorgangs | MSDN"
ms.technology: powershell
ms.openlocfilehash: 3d89dddf2fc31a9fdb1a57f21baaf757990989c7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a>Logik zum Vorbereiten der Modulabhängigkeiten während des Veröffentlichungsvorgangs
1.  Module, die als Teil von RequiredModules aufgelistet sind, werden als Abhängigkeiten betrachtet.
2.  Module, die als Teil des NestedModules-Schlüssels aufgelistet sind, dessen Modulbasis nicht Teil der angegebenen Modulbasis ist, werden als Abhängigkeiten betrachtet.

3.  Abhängigkeiten sollten in erster Linie auf dem gleichen Zielrepository vorhanden sein, ansonsten wird für den Veröffentlichungsvorgang ein Fehler ausgegeben.
    Zum Beispiel: Wenn „SnippetPx“ nicht auf dem Repository verfügbar ist, wird der unten dargestellte Fehler ausgegeben.
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  Einige Modulabhängigkeiten können extern verwaltet werden. In diesem Fall müssen sie dem Eintrag ExternalModuleDependencies im PSData-Abschnitt des Modulmanifests hinzugefügt werden.
    Im Folgenden ist ein Teil der oben angezeigten Fehlermeldung dargestellt.
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

*Während der Modulinstallation wird die oben dargestellte vorbereitete Liste der Abhängigkeiten für die Installation der Abhängigkeiten verwendet.*

*Stellen Sie sicher, dass die Abhängigkeiten Ihres Moduls unter „$env:PSModulePath“ auf Ihrem System während der Veröffentlichung verfügbar sind.*


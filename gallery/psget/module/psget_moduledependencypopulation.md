---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: gallery,powershell,cmdlet,psget
title: "Logik zum Vorbereiten der Modulabhängigkeiten während des Veröffentlichungsvorgangs | MSDN"
ms.openlocfilehash: 126cd65ac35a31f4118474bc36dac1836ec0f22e
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="logic-for-preparing-the-module-dependencies-during-publish-operation"></a><span data-ttu-id="7e37a-103">Logik zum Vorbereiten der Modulabhängigkeiten während des Veröffentlichungsvorgangs</span><span class="sxs-lookup"><span data-stu-id="7e37a-103">Logic for preparing the module dependencies during Publish operation</span></span>
1.  <span data-ttu-id="7e37a-104">Module, die als Teil von RequiredModules aufgelistet sind, werden als Abhängigkeiten betrachtet.</span><span class="sxs-lookup"><span data-stu-id="7e37a-104">Modules listed as part of RequiredModules are considered as dependencies.</span></span>
2.  <span data-ttu-id="7e37a-105">Module, die als Teil des NestedModules-Schlüssels aufgelistet sind, dessen Modulbasis nicht Teil der angegebenen Modulbasis ist, werden als Abhängigkeiten betrachtet.</span><span class="sxs-lookup"><span data-stu-id="7e37a-105">Modules listed as part of NestedModules, whose module base is not under the specified module base, are considered as dependencies.</span></span>

3.  <span data-ttu-id="7e37a-106">Abhängigkeiten sollten in erster Linie auf dem gleichen Zielrepository vorhanden sein, ansonsten wird für den Veröffentlichungsvorgang ein Fehler ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="7e37a-106">Above dependencies should be available on the same target repository, otherwise publish operation will result in an error.</span></span>
    <span data-ttu-id="7e37a-107">Zum Beispiel: Wenn „SnippetPx“ nicht auf dem Repository verfügbar ist, wird der unten dargestellte Fehler ausgegeben.</span><span class="sxs-lookup"><span data-stu-id="7e37a-107">For example: If 'SnippetPx' is not available on the repository, below error will be thrown.</span></span>
    ```powershell
    Publish-PSArtifactUtility : PowerShellGet cannot resolve the module dependency 'SnippetPx' of the module 'TypePx' on the repository 'LocalRepo'. Verify that the dependent module 'SnippetPx' is available in the repository 'LocalRepo'. If this dependent
    'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```
4.  <span data-ttu-id="7e37a-108">Einige Modulabhängigkeiten können extern verwaltet werden. In diesem Fall müssen sie dem Eintrag ExternalModuleDependencies im PSData-Abschnitt des Modulmanifests hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="7e37a-108">Some module dependencies can be managed externally, in that case they should be added to the ExternalModuleDependencies entry in the PSData section of the module manifest.</span></span>
    <span data-ttu-id="7e37a-109">Im Folgenden ist ein Teil der oben angezeigten Fehlermeldung dargestellt.</span><span class="sxs-lookup"><span data-stu-id="7e37a-109">Below part in the above error message</span></span>
    ```powershell
    If this dependent 'SnippetPx' is managed externally, add it to the ExternalModuleDependencies entry in the PSData section of the module manifest.
    ```

<span data-ttu-id="7e37a-110">*Während der Modulinstallation wird die oben dargestellte vorbereitete Liste der Abhängigkeiten für die Installation der Abhängigkeiten verwendet.*</span><span class="sxs-lookup"><span data-stu-id="7e37a-110">*During the module installation, above prepared dependencies list is used for installing the dependencies.*</span></span>

<span data-ttu-id="7e37a-111">*Stellen Sie sicher, dass die Abhängigkeiten Ihres Moduls unter „$env:PSModulePath“ auf Ihrem System während der Veröffentlichung verfügbar sind.*</span><span class="sxs-lookup"><span data-stu-id="7e37a-111">*Please ensure that your module’s dependencies are available under $env:PSModulePath on your system during publish operation.*</span></span>


---
title: Wie Sie einer finden Sie unter ein Hilfethema für den Anbieter auch Abschnitt hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858346"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="573f6-102">Hinzufügen eines Bereichs „Siehe auch“ zu einem Anbieterhilfethema</span><span class="sxs-lookup"><span data-stu-id="573f6-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="573f6-103">In diesem Abschnitt wird erläutert, wie zum Auffüllen der **Siehe auch** Abschnitt eines Hilfethemas für den Anbieter.</span><span class="sxs-lookup"><span data-stu-id="573f6-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="573f6-104">Die **Siehe auch** Abschnitt besteht aus einer Liste von Themen, die an den Anbieter beziehen oder kann helfen, den Benutzer besser verstehen und verwenden Sie den Anbieter.</span><span class="sxs-lookup"><span data-stu-id="573f6-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="573f6-105">Die Thema enthält eine Liste kann die Cmdlet-Hilfe, Hilfe durch Anbieter enthalten und ("about")-Hilfethemen in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="573f6-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="573f6-106">Sie können auch Verweise auf Bücher, Artikel und online Themen, wie eine Onlineversion des Hilfethemas aktuellen Anbieter enthalten.</span><span class="sxs-lookup"><span data-stu-id="573f6-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="573f6-107">Wenn auf Themen verwiesen wird, geben Sie den URI oder einen Suchbegriff im nur-Text aus.</span><span class="sxs-lookup"><span data-stu-id="573f6-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="573f6-108">Die `Get-Help` Cmdlet nicht verknüpfen oder Umleitung zu den Themen in der Liste.</span><span class="sxs-lookup"><span data-stu-id="573f6-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="573f6-109">Darüber hinaus die `Online` Parameter, der die `Get-Help` Cmdlet funktioniert nicht mit anbieterhilfe.</span><span class="sxs-lookup"><span data-stu-id="573f6-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="573f6-110">Im Abschnitt Siehe auch wird erstellt, aus der `RelatedLinks` Element und die darin enthaltenen Tags.</span><span class="sxs-lookup"><span data-stu-id="573f6-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="573f6-111">Das folgende XML zeigt, wie Sie die Tags hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="573f6-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="573f6-112">"Siehe auch" Themen hinzufügen</span><span class="sxs-lookup"><span data-stu-id="573f6-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="573f6-113">In der *AssemblyName*help.xml-DLL-Datei, in der `providerHelp` -Element, Hinzufügen einer `RelatedLinks` Element.</span><span class="sxs-lookup"><span data-stu-id="573f6-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="573f6-114">Die `RelatedLinks` Element muss das letzte Element in der `providerHelp` Element.</span><span class="sxs-lookup"><span data-stu-id="573f6-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="573f6-115">Nur ein `RelatedLinks` Element jedes Hilfethemas Anbieter zulässig ist.</span><span class="sxs-lookup"><span data-stu-id="573f6-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="573f6-116">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="573f6-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="573f6-117">Für jedes Thema in der **Siehe auch** Abschnitt innerhalb der `RelatedLinks` -Element, Hinzufügen einer `navigationLink` Element.</span><span class="sxs-lookup"><span data-stu-id="573f6-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="573f6-118">Klicken Sie dann in jedem `navigationLink` -Element, fügen Sie eine `linkText` -Element und ein `uri` Element.</span><span class="sxs-lookup"><span data-stu-id="573f6-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="573f6-119">Wenn Sie nicht verwenden, werden die `uri` Element können Sie ihn hinzufügen als leeres Element (\<Uri / >).</span><span class="sxs-lookup"><span data-stu-id="573f6-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="573f6-120">Beispiel:</span><span class="sxs-lookup"><span data-stu-id="573f6-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="573f6-121">Geben Sie den Namen des Themas zwischen der `linkText` Tags.</span><span class="sxs-lookup"><span data-stu-id="573f6-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="573f6-122">Wenn Sie einen URI bereitstellen, geben sie zwischen den `uri` Tags.</span><span class="sxs-lookup"><span data-stu-id="573f6-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="573f6-123">Die Onlineversion des Hilfethemas für aktuelle Anbieter zwischen an die `linkText` Tags, Typ "Online-Version:" anstelle der Name des Themas.</span><span class="sxs-lookup"><span data-stu-id="573f6-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="573f6-124">In der Regel die "Online-Version:" Link ist das erste Thema in der Themenliste auch finden Sie unter.</span><span class="sxs-lookup"><span data-stu-id="573f6-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="573f6-125">Im folgende Beispiel enthalten, siehe auch drei Themen.</span><span class="sxs-lookup"><span data-stu-id="573f6-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="573f6-126">Die erste finden Sie in der Onlineversion des aktuellen Themas.</span><span class="sxs-lookup"><span data-stu-id="573f6-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="573f6-127">Die zweite bezieht sich auf einem Windows PowerShell-Cmdlet-Hilfethemas.</span><span class="sxs-lookup"><span data-stu-id="573f6-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="573f6-128">Die dritte bezieht sich auf einem anderen Thema.</span><span class="sxs-lookup"><span data-stu-id="573f6-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,setup
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
<a id="separation-of-node-and-configuration-ids" class="xliff"></a>
# Trennung von Knoten- und Konfigurations-ID

<a id="overview" class="xliff"></a>
## Übersicht

Um bei Verwenden von DSC im Pullmodus eine flexiblere und bessere Erfahrung zu bieten, haben wir in dieser Version verschiedene Features hinzugefügt. Diese Features ermöglichen Ihnen ein flexibles Einrichten und Bereitstellen von Konfigurationen auf mehreren Knoten und zugleich das Nachverfolgen des Status und von Berichtsinformationen für jeden einzelnen Knoten. Diese Features sind wie folgt:

* Ein Konfigurationsname, der die Konfiguration für einen Computer identifiziert. Dieser Name kann von mehreren Zielknoten verwendet werden. 
* Eine Agent-ID, die einen einzelnen Knoten eindeutig identifiziert.
* Ein Registrierungsschritt, der nur erfolgt, wenn sich ein Zielknoten erstmals mit einem Pullserver verbindet.

**Hinweis:** Diese Features und Funktionen wurden hinzugefügt und ersetzen vorhandene Pullfeatures und -konzepte nicht. Sie können diese neuen Features oder die älteren mit dem neuen Pullserver in dieser Version verwenden.

Weitere Informationen finden Sie unter [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).


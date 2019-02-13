---
ms.date: 06/12/2017
keywords: wmf,powershell,setup
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678374"
---
# <a name="separation-of-node-and-configuration-ids"></a>Trennung von Knoten- und Konfigurations-ID

## <a name="overview"></a>Übersicht

Um bei Verwenden von DSC im Pullmodus eine flexiblere und bessere Erfahrung zu bieten, haben wir in dieser Version verschiedene Features hinzugefügt. Diese Features ermöglichen Ihnen ein flexibles Einrichten und Bereitstellen von Konfigurationen auf mehreren Knoten und zugleich das Nachverfolgen des Status und von Berichtsinformationen für jeden einzelnen Knoten.
Diese Features sind wie folgt:

* Ein Konfigurationsname, der die Konfiguration für einen Computer identifiziert. Dieser Name kann von mehreren Zielknoten verwendet werden.
* Eine Agent-ID, die einen einzelnen Knoten eindeutig identifiziert.
* Ein Registrierungsschritt, der nur erfolgt, wenn sich ein Zielknoten erstmals mit einem Pullserver verbindet.

**Hinweis:** Diese Features und Funktionen wurden hinzugefügt und ersetzen vorhandene Pullfeatures und -konzepte nicht. Sie können diese neuen Features oder die älteren mit dem neuen Pullserver in dieser Version verwenden.

Weitere Informationen finden Sie unter [Einrichten eines Pullclients mithilfe von Konfigurationsnamen](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).

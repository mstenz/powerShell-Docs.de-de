---
title: Erweitertes Typsystem (Übersicht)
ms.date: 07/09/2020
ms.topic: conceptual
ms.openlocfilehash: 82170bd7e8943f68141159a7ac964f9ec1b2cfbc
ms.sourcegitcommit: d26e2237397483c6333abcf4331bd82f2e72b4e3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2020
ms.locfileid: "86217940"
---
# <a name="extended-type-system-overview"></a>Erweitertes Typsystem (Übersicht)

PowerShell verwendet das **psobject** -Objekt, um die Typen von Objekten auf zweierlei Weise zu erweitern. Zuerst bietet das **psobject** -Objekt eine Möglichkeit zum Anzeigen verschiedener Sichten spezifischer Objekttypen. Dies wird als Darstellung einer angepassten Ansicht eines Objekts bezeichnet. Zweitens bietet das **psobject** -Objekt eine Möglichkeit zum Hinzufügen von Membern zu einem vorhandenen Objekt. Durch das umwickeln eines vorhandenen Objekts, das als Basisobjekt bezeichnet wird, bietet das **psobject** -Objekt ein erweitertes Typsystem (ETS), das Skript-und Cmdlet-Entwickler zum Bearbeiten von .NET-Objekten in der Shell verwenden können.

## <a name="cmdlet-and-script-development-issues"></a>Probleme bei der Cmdlet-und Skript Entwicklung

ETS löst zwei grundlegende Probleme:

Erstens verfügen einige .NET-Objekte nicht über das erforderliche Standardverhalten zum agieren als Daten zwischen Cmdlets.

- Einige .NET-Objekte sind "Meta"-Objekte (z. b. WMI-Objekte, ADO-Objekte und XML-Objekte), deren Mitglieder die darin enthaltenen Daten beschreiben. In einer Skript Umgebung handelt es sich jedoch um die darin enthaltenen Daten, nicht um die Beschreibung der enthaltenen Daten. ETS lösen dieses Problem, indem Sie das Konzept von Adaptern einführen, die das zugrunde liegende .NET-Objekt an die erwartete Standard Semantik anpassen.
- Einige .net-Objektmember sind inkonsistent benannt, stellen einen nicht ausreichenden Satz von öffentlichen Membern bereit oder stellen unzureichende Funktionen bereit. ETS lösen dieses Problem durch die Möglichkeit, das .NET-Objekt mit zusätzlichen Membern zu erweitern.

Zweitens ist die PowerShell-Skriptsprache _typlos_ , da eine Variable nicht für einen bestimmten Typ deklariert werden muss. Das heißt, die Variablen, die ein Skriptentwickler erstellt, sind naturgemäß _typlos_. Das PowerShell-System ist jedoch "typgesteuert", da es davon abhängt, dass ein Typname für grundlegende Vorgänge, wie z. b. die Ausgabe von Ergebnissen oder die Sortierung, verwendet werden muss.

Daher muss ein Skriptentwickler die Möglichkeit haben, den Typ einer Ihrer Variablen zu erstellen und einen eigenen Satz dynamisch typisierter "Objekte" zu erstellen, die Eigenschaften und Methoden enthalten und am typgesteuerten System beteiligt sein können. ETS lösen dieses Problem, indem Sie ein gemeinsames Objekt für die Skriptsprache bereitstellen, das die Möglichkeit hat, den Typ dynamisch einzugeben und Elemente dynamisch hinzuzufügen.

Im Grunde löst ETS das zuvor erwähnte Problem durch Bereitstellen des **psobject** -Objekts, das als Grundlage für den gesamten Objektzugriff von der Skriptsprache fungiert und eine Standard Abstraktion für den Cmdlet-Entwickler bereitstellt.

### <a name="cmdlet-developers"></a>Cmdlet-Entwickler

Für die Cmdlet-Entwickler bietet ETS die folgende Unterstützung:

- Die Abstraktionen, die mithilfe des **psobject** -Objekts auf generische Weise mit Objekten arbeiten. ETS bietet auch die Möglichkeit, bei Bedarf diese Abstraktionen zu überschreiten.
- Die Mechanismen zum Erstellen eines Standard Verhaltens für Formatierung, Sortierung, Serialisierung und andere System Manipulationen Ihres Objekt Typs mithilfe eines bekannten Satzes erweiterter Member.
- Die Methode zum Arbeiten mit einem Objekt, das die gleiche Semantik wie die Skriptsprache verwendet, mithilfe eines LanguagePrimitives-Objekts.
- Das bedeutet, dass Sie eine Hash Tabelle dynamisch "eingeben", damit der Rest des Systems effektiv verarbeitet werden kann.

### <a name="script-developers"></a>Skriptentwickler

Für die Skriptentwickler bietet ETS die folgende Unterstützung:

- Die Möglichkeit, auf einen zugrunde liegenden Objekttyp mit derselben Syntax () zu verweisen `$a.x` .
- Die Möglichkeit, auf die über die vom **psobject** -Objekt bereitgestellte Abstraktion zuzugreifen (z. b. das Zugreifen auf nur angepasste Member oder das Zugreifen auf das Basisobjekt selbst).
- Die Möglichkeit, bekannte Member zu definieren, die die Formatierung, Sortierung, Serialisierung und andere Manipulationen einer Objektinstanz oder eines Typs steuern.
- Das bedeutet, ein Objekt als bestimmten Typ zu benennen und somit die Vererbung der typbasierten Member zu steuern.
- Die Möglichkeit, erweiterte Member hinzuzufügen, zu entfernen und zu ändern.
- Die Möglichkeit, das **psobject** -Objekt selbst zu manipulieren, wenn dies erforderlich ist.

## <a name="the-psobject-class"></a>Die psobject-Klasse

Das **psobject** -Objekt ist die Grundlage für den gesamten Objektzugriff von der Skriptsprache und stellt eine Standard Abstraktion für den Cmdlet-Entwickler bereit. Sie enthält ein Basisobjekt (ein .NET-Objekt) und alle Instanzmember (Member, insbesondere Erweiterte Member, die auf einer bestimmten Objektinstanz vorhanden sind, und nicht notwendigerweise auf anderen Objekten desselben Typs). Abhängig vom Typ des Basis Objekts kann das **psobject** -Objekt auch impliziten und expliziten Zugriff auf angepasste Member sowie auf beliebige typbasierte Erweiterte Member bereitstellen.

Das **psobject** -Objekt bietet die folgenden Mechanismen:

- Die Fähigkeit zum Erstellen eines **psobject** mit oder ohne Basisobjekt.
- Die Möglichkeit, auf alle Member jedes konstruierten **psobject** -Objekts über einen allgemeinen Suchalgorithmus zuzugreifen, und die Möglichkeit, diesen Algorithmus bei Bedarf zu überschreiben.
- Die Möglichkeit, die Typnamen der konstruierten **psobject** -Objekte zu erhalten und festzulegen, damit Skripts und Cmdlets auf ähnliche **psobject** -Objekte mit demselben Typnamen verweisen können, unabhängig vom Typ Ihres Basis Objekts.

### <a name="how-to-construct-a-psobject"></a>Erstellen eines psobject

In der folgenden Liste wird beschrieben, wie Sie ein **psobject** -Objekt erstellen:

- Durch Aufrufen des Konstruktors **psobject** . #ctor wird ein neues **psobject** -Objekt mit einem Base-Objekt von pscustomobject erstellt. Ein Basisobjekt dieses Typs gibt an, dass das **psobject** -Objekt kein sinnvolles Basisobjekt aufweist. Ein **psobject** -Objekt mit diesem Typ von Base-Object bietet jedoch einen Eigenschaften Behälter, der von Cmdlet-Entwicklern durch Hinzufügen von erweiterten Membern hilfreich gefunden werden kann.

Entwickler können auch den Objekttyp Name angeben, der es diesem Objekt ermöglicht, seine erweiterten Member mit anderen **psobject** -Objekten desselben Typnamens freizugeben.

- Durch Aufrufen des **psobject** . #ctor (System. Object)-Konstruktors wird ein neues **psobject** -Objekt mit einem Basisobjekt des Typs "System. Object" erstellt.

  In diesem Fall ist der Typname für das erstellte Objekt eine Auflistung der abderivationshierarchie des Base-Object. Beispielsweise enthält der Typname für das **psobject** , das ein ProcessInfo-Basisobjekt enthält, die folgenden Namen:

  - System.Diagnostics.Process
  - System. ComponentModel. Component
  - System.MarshalByRefObject
  - System.Object

- **Psobject** wird aufgerufen. Die aspsobject (System. Object)-Methode erstellt ein neues **psobject** -Objekt auf Grundlage eines angegebenen-Objekts.

  Wenn das angegebene Objekt vom Typ "System. Object" ist, wird das angegebene Objekt als Basisobjekt für das neue **psobject** -Objekt verwendet. Wenn das angegebene Objekt bereits ein **psobject** -Objekt ist, wird das angegebene Objekt unverändert zurückgegeben.

### <a name="base-adapted-and-extended-members"></a>Basis-, angepasste und erweiterte Member

Im Prinzip verwendet ETS die folgenden Begriffe, um die Beziehung zwischen den ursprünglichen Membern des Basis Objekts und den von PowerShell hinzugefügten Membern anzuzeigen. Weitere Informationen zu den spezifischen Typen von Membern, die vom **psobject** -Objekt verwendet werden, finden Sie unter [psobject-Klasse](/dotnet/api/system.management.automation.psobject).

#### <a name="base-object-members"></a>Basisobjekt Elemente

Wenn das Basisobjekt beim Erstellen der **psobject** -Objekte angegeben wird, werden die Elemente des Basis Objekts über die Members-Eigenschaft zur Verfügung gestellt.

#### <a name="adapted-members"></a>Angepasste Member

Wenn ein Basisobjekt ein Meta-Objekt ist, das Daten in einer generischen Weise enthält, deren Eigenschaften ihre enthaltenen Daten beschreiben, passt ETS diese Objekte an eine Ansicht an, die den direkten Zugriff auf die Daten durch angepasste Member des **psobject** -Objekts ermöglicht. Auf angepasste Member und Basisobjekt Elemente wird über die Members-Eigenschaft zugegriffen.

#### <a name="extended-members"></a>Erweiterte Member

Zusätzlich zu den Membern, die aus dem Basisobjekt oder den von PowerShell erstellten angepassten Membern verfügbar gemacht werden, kann ein **psobject** auch erweiterte Member definieren, die das ursprüngliche Basisobjekt mit zusätzlichen Informationen erweitern, die in der Skript Umgebung nützlich sind.

Beispielsweise nehmen alle Kern-Cmdlets, die von PowerShell bereitgestellt werden, wie z. b. die Cmdlets Get-Content und Set-Content, einen path-Parameter an. Um sicherzustellen, dass diese Cmdlets und andere mit Objekten unterschiedlicher Typen arbeiten können, kann diesen Objekten ein pfadmember hinzugefügt werden, sodass Sie alle Ihre Informationen auf eine gängige Weise angeben. Dieser erweiterte pfadmember stellt sicher, dass die Cmdlets für alle diese Typen funktionieren, auch wenn die Basisklasse möglicherweise keinen pfadmember hat.

Auf Erweiterte Member, angepasste Member und Basisobjekt Elemente wird alle über die Members-Eigenschaft zugegriffen.

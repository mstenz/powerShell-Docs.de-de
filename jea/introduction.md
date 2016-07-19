---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "Einführung"
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6b5107b7222708dcceff14bc26f0e12ef98d728
ms.openlocfilehash: 00d568234b1453b9161b60d20117374ee4111ab3

---

# Einführung

##  **Beweggründe**  
Wenn Sie einer Person privilegierten Zugriff auf Ihre Systeme gewähren, erweitern Sie Ihre Vertrauensstellungsgrenze auf diese Person.
Dies birgt Risiken – Administratoren sind eine Angriffsfläche.
Sowohl Angriffe als auch gestohlene Anmeldeinformationen sind reale und nicht seltene Gefahren.

##  **Das ist kein neues Problem.**  
Sie sind sicher mit der Regel der geringsten Rechte vertraut, und Sie verwenden bestimmt eine Form der rollenbasierten Zugriffssteuerung (Role-Based Access Control, RBAC) bei Anwendungen, die diese bereitstellen.
Effektivität und Verwaltungsfreundlichkeit solcher Lösungen sind jedoch häufig durch ihren Funktionsumfang und ihre Ungenauigkeit begrenzt.
Darüber hinaus weist die rollenbasierte Zugriffssteuerung Lücken auf.
In Windows beispielsweise ist der privilegierte Zugriff im Großen und Ganzen ein binärer Schalter, sodass Sie unnötige Berechtigungen erteilen müssen, wenn Sie Benutzer zur Administratorengruppe hinzufügen.

##  **Just Enough Administration (JEA)** 
Bietet eine Plattform für rollenbasierte Zugriffssteuerung (Role-based Access Control, RBAC) durch PowerShell-Remoting.
*Damit können bestimmte Benutzer bestimmte administrative Aufgaben auf Servern ausführen, ohne dass ihnen Administratorrechte gewährt werden müssen.*
So können Sie die Lücken zwischen Ihren vorhandenen RBAC-Lösungen schließen, und die Verwaltung dieser Einstellungen wird vereinfacht.




<!--HONumber=Jul16_HO1-->



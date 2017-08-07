---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Erste Schritte mit Windows PowerShell
ms.assetid: b0e2ad92-875f-421d-b612-f624e644aa69
ms.openlocfilehash: 8dbdd5d7b2dcb80e5562ff0f0f211b2baf5357cf
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="getting-started-with-windows-powershell"></a><span data-ttu-id="ea7f4-103">Erste Schritte mit Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea7f4-103">Getting Started with Windows PowerShell</span></span>
<span data-ttu-id="ea7f4-104">Windows PowerShell ist eine Windows-Befehlszeilenshell, die insbesondere für Systemadministratoren konzipiert ist.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-104">Windows PowerShell is a Windows command-line shell designed especially for system administrators.</span></span> <span data-ttu-id="ea7f4-105">Windows PowerShell umfasst eine interaktive Eingabeaufforderung und eine Skriptumgebung, die einzeln oder in Kombination verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-105">Windows PowerShell includes an interactive prompt and a scripting environment that can be used independently or in combination.</span></span>

<span data-ttu-id="ea7f4-106">Anders als die meisten Shells, in denen Text akzeptiert und zurückgegeben wird, setzt Windows PowerShell auf der .NET Framework Common Language Runtime (CLR) und auf .NET Framework auf und akzeptiert .NET Framework-Objekte bzw. gibt .NET Framework-Objekte zurück.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-106">Unlike most shells, which accept and return text, Windows PowerShell is built on top of the .NET Framework common language runtime (CLR) and the .NET Framework, and accepts and returns .NET Framework objects.</span></span> <span data-ttu-id="ea7f4-107">Diese grundlegende Änderung in der Umgebung bedingt völlig neue Tools und Methoden für die Verwaltung und Konfiguration von Windows.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-107">This fundamental change in the environment brings entirely new tools and methods to the management and configuration of Windows.</span></span>

<span data-ttu-id="ea7f4-108">Windows PowerShell führt das Konzept eines Cmdlets (ausgesprochen als „Command-let“) ein. Dies ist ein einfaches Einzelfunktions-Befehlszeilentool, das in die Shell integriert ist.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-108">Windows PowerShell introduces the concept of a cmdlet (pronounced "command-let"), a simple, single-function command-line tool built into the shell.</span></span> <span data-ttu-id="ea7f4-109">Sie können jedes Cmdlet einzeln verwenden, aber deren Leistungsfähigkeit wird freigesetzt, wenn Sie diese einfachen Tools in Kombination verwenden, um komplexe Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-109">You can use each cmdlet separately, but their power is realized when you use these simple tools in combination to perform complex tasks.</span></span> <span data-ttu-id="ea7f4-110">Windows PowerShell umfasst mehr als einhundert grundlegende Kerncmdlets, und Sie können eigene Cmdlets schreiben und diese für andere Benutzer freigeben.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-110">Windows PowerShell includes more than one hundred basic core cmdlets, and you can write your own cmdlets and share them with other users.</span></span>

<span data-ttu-id="ea7f4-111">Ähnlich wie viele Shells ermöglicht Windows PowerShell Ihnen Zugriff auf das Dateisystem auf dem Computer.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-111">Like many shells, Windows PowerShell gives you access to the file system on the computer.</span></span> <span data-ttu-id="ea7f4-112">Darüber hinaus bieten Windows PowerShell-*Anbieter* Ihnen die Möglichkeit, auf andere Datenspeicher, etwa die Registrierung und den Zertifikatspeicher für digitale Signaturen, so einfach zuzugreifen wie auf das Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-112">In addition, Windows PowerShell *providers* enable you to access other data stores, such as the registry and the digital signature certificate stores, as easily as you access the file system.</span></span>

<span data-ttu-id="ea7f4-113">Dieses „Erste Schritte“-Handbuch bietet eine Einführung in Windows PowerShell: die Sprache, die Cmdlets, die Anbieter und die Verwendung von Objekten.</span><span class="sxs-lookup"><span data-stu-id="ea7f4-113">This Getting Started guide provides an introduction to Windows PowerShell: the language, the cmdlets, the providers, and the use of objects.</span></span>

<span data-ttu-id="ea7f4-114">Inhalte dieses Themas:</span><span class="sxs-lookup"><span data-stu-id="ea7f4-114">In this topic:</span></span>

-   [<span data-ttu-id="ea7f4-115">Windows PowerShell-Systemanforderungen</span><span class="sxs-lookup"><span data-stu-id="ea7f4-115">Windows PowerShell System Requirements</span></span>](../setup/Windows-PowerShell-System-Requirements.md)

-   [<span data-ttu-id="ea7f4-116">Installieren von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea7f4-116">Installing Windows PowerShell</span></span>](../setup/Installing-Windows-PowerShell.md)

-   [<span data-ttu-id="ea7f4-117">Starten von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea7f4-117">Starting Windows PowerShell</span></span>](../setup/Starting-Windows-PowerShell.md)

-   [<span data-ttu-id="ea7f4-118">Vorbereiten der Verwendung von Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ea7f4-118">Getting Ready to Use Windows PowerShell</span></span>](Getting-Ready-to-Use-Windows-PowerShell.md)

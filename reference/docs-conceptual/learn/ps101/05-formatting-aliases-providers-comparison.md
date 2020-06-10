---
title: Formatierung, Aliase, Anbieter, Vergleich
ms.date: 06/02/2020
ms.topic: guide
ms.custom: Contributor-mikefrobbins
ms.reviewer: mirobb
ms.openlocfilehash: eb23b048a50f10ea83d156c0499772b1be439336
ms.sourcegitcommit: 0d958eac5bde5ccf5ee2c1bac4f009a63bf71368
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2020
ms.locfileid: "84438001"
---
# <a name="chapter-5---formatting-aliases-providers-comparison"></a><span data-ttu-id="d11e0-102">Kapitel 5: Formatierung, Aliase, Anbieter, Vergleich</span><span class="sxs-lookup"><span data-stu-id="d11e0-102">Chapter 5 - Formatting, aliases, providers, comparison</span></span>

## <a name="requirements"></a><span data-ttu-id="d11e0-103">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="d11e0-103">Requirements</span></span>

<span data-ttu-id="d11e0-104">Das SQL Server PowerShell-Modul ist für einige der in diesem Kapitel gezeigten Beispiele erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d11e0-104">The SQL Server PowerShell module is required by some of the examples shown in this chapter.</span></span> <span data-ttu-id="d11e0-105">Das Modul wird als Bestandteil von [SQL Server Management Studio (SSMS)][SMSS] installiert.</span><span class="sxs-lookup"><span data-stu-id="d11e0-105">The module installs as part of [SQL Server Management Studio (SMSS)][SMSS].</span></span> <span data-ttu-id="d11e0-106">Es wird auch in nachfolgenden Kapiteln verwendet.</span><span class="sxs-lookup"><span data-stu-id="d11e0-106">It's also used in subsequent chapters.</span></span> <span data-ttu-id="d11e0-107">Laden Sie es auf Ihren Windows 10-Laborumgebungscomputer herunter, und installieren Sie es.</span><span class="sxs-lookup"><span data-stu-id="d11e0-107">Download and install it on your Windows 10 lab environment computer.</span></span>

## <a name="format-right"></a><span data-ttu-id="d11e0-108">Rechts formatieren</span><span class="sxs-lookup"><span data-stu-id="d11e0-108">Format Right</span></span>

<span data-ttu-id="d11e0-109">In Kapitel 4 haben Sie gelernt, so weit wie möglich nach links zu filtern.</span><span class="sxs-lookup"><span data-stu-id="d11e0-109">In Chapter 4, you learned to filter as far to the left as possible.</span></span> <span data-ttu-id="d11e0-110">Die Regel für manuelles Formatieren der Ausgabe eines Befehls ähnelt dieser Regel, außer dass sie so weit wie möglich auf der rechten Seite vorkommen muss.</span><span class="sxs-lookup"><span data-stu-id="d11e0-110">The rule for manually formatting a command's output is similar to that rule except it needs to occur as far to the right as possible.</span></span>

<span data-ttu-id="d11e0-111">Die gängigsten Formatierungsbefehle sind `Format-Table` und `Format-List`.</span><span class="sxs-lookup"><span data-stu-id="d11e0-111">The most common format commands are `Format-Table` and `Format-List`.</span></span> <span data-ttu-id="d11e0-112">`Format-Wide` und `Format-Custom` können auch verwendet werden, sind jedoch weniger gängig.</span><span class="sxs-lookup"><span data-stu-id="d11e0-112">`Format-Wide` and `Format-Custom` can also be used, but are less common.</span></span>

<span data-ttu-id="d11e0-113">Wie in Kapitel 3 erwähnt, wird ein Befehl, der mehr als vier Eigenschaften zurückgibt, standardmäßig zu einer Liste, wenn keine benutzerdefinierte Formatierung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d11e0-113">As mentioned in Chapter 3, a command that returns more than four properties defaults to a list unless custom formatting is used.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can*
```

```Output
Status              : Running
DisplayName         : Windows Time
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
```

<span data-ttu-id="d11e0-114">Verwenden Sie das Cmdlet `Format-Table`, um die Formatierung manuell außer Kraft zu setzen und die Ausgabe in einer Tabelle anstatt in einer Liste anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-114">Use the `Format-Table` cmdlet to manually override the formatting and show the output in a table instead of a list.</span></span>

```powershell
Get-Service -Name w32time | Select-Object -Property Status, DisplayName, Can* |
Format-Table
```

```Output
 Status DisplayName  CanPauseAndContinue CanShutdown CanStop
 ------ -----------  ------------------- ----------- -------
Running Windows Time               False        True    True
```

<span data-ttu-id="d11e0-115">Die Standardausgabe für `Get-Service` sind drei Eigenschaften in einer Tabelle.</span><span class="sxs-lookup"><span data-stu-id="d11e0-115">The default output for `Get-Service` is three properties in a table.</span></span>

```powershell
Get-Service -Name w32time
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  w32time            Windows Time
```

<span data-ttu-id="d11e0-116">Verwenden Sie das Cmdlet `Format-List`, um die Standardformatierung außer Kraft zu setzen und die Ergebnisse in einer Liste zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="d11e0-116">Use the `Format-List` cmdlet to override the default formatting and return the results in a list.</span></span>

```powershell
Get-Service -Name w32time | Format-List
```

```Output
Name                : w32time
DisplayName         : Windows Time
Status              : Running
DependentServices   : {}
ServicesDependedOn  : {}
CanPauseAndContinue : False
CanShutdown         : True
CanStop             : True
ServiceType         : Win32ShareProcess
```

<span data-ttu-id="d11e0-117">Beachten Sie, dass durch das einfache Weiterleiten von `Get-Service` an `Format-List` per Pipeline zusätzliche Eigenschaften zurückgegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="d11e0-117">Notice that simply piping `Get-Service` to `Format-List` made it return additional properties.</span></span> <span data-ttu-id="d11e0-118">Dies tritt nicht bei jedem Befehl auf, was an der Weise liegt, in der die Art der Formatierung für diesen bestimmten Befehl im Hintergrund eingerichtet ist.</span><span class="sxs-lookup"><span data-stu-id="d11e0-118">This doesn't occur with every command because of the way the formatting for that particular command is set up behind the scenes.</span></span>

<span data-ttu-id="d11e0-119">Die Hauptsache, derer Sie sich bei den Formatierungs-Cmdlets bewusst sein sollten, ist, dass sie Formatobjekte erzeugen, die sich von normalen Objekten in PowerShell unterscheiden.</span><span class="sxs-lookup"><span data-stu-id="d11e0-119">The number one thing to be aware of with the format cmdlets is they produce format objects that are different than normal objects in PowerShell.</span></span>

```powershell
Get-Service -Name w32time | Format-List | Get-Member
```

```Output
   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
autosizeInfo                            Property   Microsoft.PowerShell.Commands.Inter...
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
pageFooterEntry                         Property   Microsoft.PowerShell.Commands.Inter...
pageHeaderEntry                         Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupStartData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
shapeInfo                               Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEntryData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
formatEntryInfo                         Property   Microsoft.PowerShell.Commands.Inter...
outOfBand                               Property   bool outOfBand {get;set;}
writeStream                             Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.GroupEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...

   TypeName: Microsoft.PowerShell.Commands.Internal.Format.FormatEndData

Name                                    MemberType Definition
----                                    ---------- ----------
Equals                                  Method     bool Equals(System.Object obj)
GetHashCode                             Method     int GetHashCode()
GetType                                 Method     type GetType()
ToString                                Method     string ToString()
ClassId2e4f51ef21dd47e99d3c952918aff9cd Property   string ClassId2e4f51ef21dd47e99d3c9...
groupingEntry                           Property   Microsoft.PowerShell.Commands.Inter...
```

<span data-ttu-id="d11e0-120">Dies bedeutet, dass Formatierungsbefehle nicht per Pipeline an die meisten anderen Befehle weitergeleitet werden können.</span><span class="sxs-lookup"><span data-stu-id="d11e0-120">What this means is format commands can't be piped to most other commands.</span></span> <span data-ttu-id="d11e0-121">Sie können per Pipeline an einige der `Out-*`-Befehle weitergeleitet werden, aber das ist es auch schon.</span><span class="sxs-lookup"><span data-stu-id="d11e0-121">They can be piped to some of the `Out-*` commands, but that's about it.</span></span> <span data-ttu-id="d11e0-122">Aus diesem Grund sollten Sie jegliche Formatierung am Ende der Zeile (rechts formatieren) vornehmen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-122">This is why you want to perform any formatting at the very end of the line (format right).</span></span>

## <a name="aliases"></a><span data-ttu-id="d11e0-123">Aliase</span><span class="sxs-lookup"><span data-stu-id="d11e0-123">Aliases</span></span>

<span data-ttu-id="d11e0-124">Ein Alias ist in PowerShell ein kürzerer Name für einen Befehl.</span><span class="sxs-lookup"><span data-stu-id="d11e0-124">An alias in PowerShell is a shorter name for a command.</span></span> <span data-ttu-id="d11e0-125">PowerShell umfasst eine Reihe von integrierten Aliasnamen, doch Sie können auch eigene Aliase definieren.</span><span class="sxs-lookup"><span data-stu-id="d11e0-125">PowerShell includes a set of built-in aliases and you can also define your own aliases.</span></span>

<span data-ttu-id="d11e0-126">Mit dem Cmdlet `Get-Alias` können Sie Aliase abrufen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-126">The `Get-Alias` cmdlet is used to find aliases.</span></span> <span data-ttu-id="d11e0-127">Wenn Sie den Alias für einen Befehl bereits kennen, wird der Parameter **Name** verwendet, um zu bestimmen, welchem Befehl der Alias zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="d11e0-127">If you already know the alias for a command, the **Name** parameter is used to determine what command the alias is associated with.</span></span>

```powershell
Get-Alias -Name gcm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
```

<span data-ttu-id="d11e0-128">Für den Wert des Parameters **Name** können mehrere Aliase angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="d11e0-128">Multiple aliases can be specified for the value of the **Name** parameter.</span></span>

```powershell
Get-Alias -Name gcm, gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="d11e0-129">Sie werden häufig feststellen, dass der Parameter **Name** ausgelassen wird, weil es sich um einen Positionsparameter handelt.</span><span class="sxs-lookup"><span data-stu-id="d11e0-129">You'll often see the **Name** parameter omitted since it's a positional parameter.</span></span>

```powershell
Get-Alias gm
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gm -> Get-Member
```

<span data-ttu-id="d11e0-130">Wenn Sie Aliase für einen Befehl suchen möchten, müssen Sie den Parameter **Definition** verwenden.</span><span class="sxs-lookup"><span data-stu-id="d11e0-130">If you want to find aliases for a command, you'll need to use the **Definition** parameter.</span></span>

```powershell
Get-Alias -Definition Get-Command, Get-Member
```

```Output
CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           gcm -> Get-Command
Alias           gm -> Get-Member
```

<span data-ttu-id="d11e0-131">Der Parameter **Definition-** kann nicht als Positionsparameter verwendet werden, weshalb er angegeben werden muss.</span><span class="sxs-lookup"><span data-stu-id="d11e0-131">The **Definition** parameter can't be used positionally so it must be specified.</span></span>

<span data-ttu-id="d11e0-132">Aliase können Ihnen ein paar Tastatureingaben ersparen und sind gut geeignet, wenn Sie Befehle in die Konsole eingeben.</span><span class="sxs-lookup"><span data-stu-id="d11e0-132">Aliases can save you a few keystrokes and they're fine when you're typing commands into the console.</span></span>
<span data-ttu-id="d11e0-133">Sie sollten nicht in Skripts oder Code verwendet werden, die bzw. den Sie speichern oder mit anderen teilen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-133">They shouldn't be used in scripts or any code that you're saving or sharing with others.</span></span> <span data-ttu-id="d11e0-134">Wie in diesem Buch bereits erwähnt, ist die Verwendung vollständiger Cmdlet- und Parameternamen selbsterklärend und leichter zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-134">As mentioned earlier in this book, using full cmdlet and parameter names is self-documenting and easier to understand.</span></span>

<span data-ttu-id="d11e0-135">Gehen Sie beim Erstellen Ihrer eigenen Aliase mit Bedacht vor, da Sie nur in Ihrer aktuellen PowerShell-Sitzung auf Ihrem Computer existieren.</span><span class="sxs-lookup"><span data-stu-id="d11e0-135">Use caution when creating your own aliases because they'll only exist in your current PowerShell session on your computer.</span></span>

## <a name="providers"></a><span data-ttu-id="d11e0-136">Anbieter</span><span class="sxs-lookup"><span data-stu-id="d11e0-136">Providers</span></span>

<span data-ttu-id="d11e0-137">Ein Anbieter ist in PowerShell eine Schnittstelle, die einen dateisystemähnlichen Zugriff auf einen Datenspeicher zulässt.</span><span class="sxs-lookup"><span data-stu-id="d11e0-137">A provider in PowerShell is an interface that allows file system like access to a datastore.</span></span> <span data-ttu-id="d11e0-138">Es gibt eine Reihe integrierter Anbieter in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d11e0-138">There are a number of built-in providers in PowerShell.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
Certificate          ShouldProcess                      {Cert}
WSMan                Credentials                        {WSMan}
```

<span data-ttu-id="d11e0-139">Wie Sie in den vorherigen Ergebnissen sehen können, gibt es integrierte Anbieter für die Registrierung, für Aliase, Umgebungsvariablen, das Dateisystem, Funktionen, Variablen, Zertifikate und WSMan.</span><span class="sxs-lookup"><span data-stu-id="d11e0-139">As you can see in the previous results, there are built-in providers for the registry, aliases, environment variables, the file system, functions, variables, certificates, and WSMan.</span></span>

<span data-ttu-id="d11e0-140">Die tatsächlichen Laufwerke, die diese Anbieter verwenden, um Ihren jeweiligen Datenspeicher verfügbar zu machen, können Sie mit dem Cmdlet `Get-PSDrive` ermitteln.</span><span class="sxs-lookup"><span data-stu-id="d11e0-140">The actual drives that these providers use to expose their datastore can be determined with the `Get-PSDrive` cmdlet.</span></span> <span data-ttu-id="d11e0-141">Das Cmdlet `Get-PSDrive` zeigt nicht nur Laufwerke an, die von Anbietern verfügbar gemacht werden, sondern auch logische Windows-Laufwerke, einschließlich Laufwerken, die Netzwerkfreigaben zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="d11e0-141">The `Get-PSDrive` cmdlet not only displays drives exposed by providers, but it also displays Windows logical drives including drives mapped to network shares.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
Alias                                  Alias
C                  14.41        112.10 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="d11e0-142">Module von Drittanbietern wie das Active Directory PowerShell-Modul und das SQLServer PowerShell-Modul fügen sowohl einen eigenen PowerShell-Anbieter als auch ein PSDrive hinzu.</span><span class="sxs-lookup"><span data-stu-id="d11e0-142">Third-party modules such as the Active Directory PowerShell module and the SQLServer PowerShell module both add their own PowerShell provider and PSDrive.</span></span>

<span data-ttu-id="d11e0-143">Importieren Sie die Active Directory- und SQL Server PowerShell-Module.</span><span class="sxs-lookup"><span data-stu-id="d11e0-143">Import the Active Directory and SQL Server PowerShell modules.</span></span>

```powershell
Import-Module -Name ActiveDirectory, SQLServer
```

<span data-ttu-id="d11e0-144">Überprüfen Sie, ob zusätzliche PowerShell-Anbieter hinzugefügt wurden.</span><span class="sxs-lookup"><span data-stu-id="d11e0-144">Check to see if any additional PowerShell providers were added.</span></span>

```powershell
Get-PSProvider
```

```Output
Name                 Capabilities                       Drives
----                 ------------                       ------
Registry             ShouldProcess, Transactions        {HKLM, HKCU}
Alias                ShouldProcess                      {Alias}
Environment          ShouldProcess                      {Env}
FileSystem           Filter, ShouldProcess, Credentials {C, A, D}
Function             ShouldProcess                      {Function}
Variable             ShouldProcess                      {Variable}
ActiveDirectory      Include, Exclude, Filter, Shoul... {AD}
SqlServer            Credentials                        {SQLSERVER}
```

<span data-ttu-id="d11e0-145">Beachten Sie, dass im vorherigen Resultset jetzt zwei neue PowerShell-Anbieter vorhanden sind, einer für Active Directory und einer für SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d11e0-145">Notice that in the previous set of results, two new PowerShell providers now exist, one for Active Directory and another one for SQL Server.</span></span>

<span data-ttu-id="d11e0-146">Ein PSDrive für jedes dieser Module wurde ebenfalls hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d11e0-146">A PSDrive for each of those modules was also added.</span></span>

```powershell
Get-PSDrive
```

```Output
Name           Used (GB)     Free (GB) Provider      Root
----           ---------     --------- --------      ----
A                                      FileSystem    A:\
AD                                     ActiveDire... //RootDSE/
Alias                                  Alias
C                  19.38        107.13 FileSystem    C:\
Cert                                   Certificate   \
D                                      FileSystem    D:\
Env                                    Environment
Function                               Function
HKCU                                   Registry      HKEY_CURRENT_USER
HKLM                                   Registry      HKEY_LOCAL_MACHINE
SQLSERVER                              SqlServer     SQLSERVER:\
Variable                               Variable
WSMan                                  WSMan
```

<span data-ttu-id="d11e0-147">Der Zugriff auf PSDrives erfolgt genauso wie auf ein herkömmliches Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="d11e0-147">PSDrives can be accessed just like a traditional file system.</span></span>

```powershell
Get-ChildItem -Path Cert:\LocalMachine\CA
```

```Output
   PSParentPath: Microsoft.PowerShell.Security\Certificate::LocalMachine\CA

Thumbprint                                Subject
----------                                -------
FEE449EE0E3965A5246F000E87FDE2A065FD89D4  CN=Root Agency
D559A586669B08F46A30A133F8A9ED3D038E2EA8  OU=www.verisign.com/CPS Incorporated LIABI...
109F1CAED645BB78B3EA2B94C0697C740733031C  CN=Microsoft Windows Hardware Compatibility,...
```

## <a name="comparison-operators"></a><span data-ttu-id="d11e0-148">Vergleichsoperatoren</span><span class="sxs-lookup"><span data-stu-id="d11e0-148">Comparison Operators</span></span>

<span data-ttu-id="d11e0-149">PowerShell enthält eine Reihe von Vergleichsoperatoren, die verwendet werden, um Werte zu vergleichen oder um Werte zu suchen, die bestimmten Mustern entsprechen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-149">PowerShell contains a number of comparison operators that are used to compare values or find values that match certain patterns.</span></span> <span data-ttu-id="d11e0-150">Tabelle 5-1 enthält eine Liste der Vergleichsoperatoren in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d11e0-150">Table 5-1 contains a list of comparison operators in PowerShell.</span></span>

|    <span data-ttu-id="d11e0-151">Operator</span><span class="sxs-lookup"><span data-stu-id="d11e0-151">Operator</span></span>    |                          <span data-ttu-id="d11e0-152">Definition</span><span class="sxs-lookup"><span data-stu-id="d11e0-152">Definition</span></span>                          |
| -------------- | ------------------------------------------------------------ |
| `-eq`          | <span data-ttu-id="d11e0-153">Gleich</span><span class="sxs-lookup"><span data-stu-id="d11e0-153">Equal to</span></span>                                                     |
| `-ne`          | <span data-ttu-id="d11e0-154">Ungleich</span><span class="sxs-lookup"><span data-stu-id="d11e0-154">Not equal to</span></span>                                                 |
| `-gt`          | <span data-ttu-id="d11e0-155">Größer als</span><span class="sxs-lookup"><span data-stu-id="d11e0-155">Greater than</span></span>                                                 |
| `-ge`          | <span data-ttu-id="d11e0-156">Größer als oder gleich</span><span class="sxs-lookup"><span data-stu-id="d11e0-156">Greater than or equal to</span></span>                                     |
| `-lt`          | <span data-ttu-id="d11e0-157">Kleiner als</span><span class="sxs-lookup"><span data-stu-id="d11e0-157">Less than</span></span>                                                    |
| `-le`          | <span data-ttu-id="d11e0-158">Kleiner als oder gleich</span><span class="sxs-lookup"><span data-stu-id="d11e0-158">Less than or equal to</span></span>                                        |
| `-Like`        | <span data-ttu-id="d11e0-159">Entspricht unter Verwendung des Platzhalterzeichens `*`</span><span class="sxs-lookup"><span data-stu-id="d11e0-159">Match using the `*` wildcard character</span></span>                       |
| `-NotLike`     | <span data-ttu-id="d11e0-160">Entspricht nicht unter Verwendung des Platzhalterzeichens `*`</span><span class="sxs-lookup"><span data-stu-id="d11e0-160">Does not match using the `*` wildcard character</span></span>              |
| `-Match`       | <span data-ttu-id="d11e0-161">Entspricht dem angegebenen regulären Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="d11e0-161">Matches the specified regular expression</span></span>                     |
| `-NotMatch`    | <span data-ttu-id="d11e0-162">Entspricht nicht dem angegebenen regulären Ausdruck.</span><span class="sxs-lookup"><span data-stu-id="d11e0-162">Does not match the specified regular expression</span></span>              |
| `-Contains`    | <span data-ttu-id="d11e0-163">Bestimmt, ob eine Sammlung einen angegebenen Wert enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-163">Determines if a collection contains a specified value</span></span>        |
| `-NotContains` | <span data-ttu-id="d11e0-164">Bestimmt, ob die Auflistung einen bestimmten Wert nicht enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-164">Determines if a collection does not contain a specific value</span></span> |
| `-In`          | <span data-ttu-id="d11e0-165">Bestimmt, ob sich ein angegebener Wert in einer Sammlung befindet.</span><span class="sxs-lookup"><span data-stu-id="d11e0-165">Determines if a specified value is in a collection</span></span>           |
| `-NotIn`       | <span data-ttu-id="d11e0-166">Bestimmt, ob sich ein angegebener Wert nicht in einer Sammlung befindet.</span><span class="sxs-lookup"><span data-stu-id="d11e0-166">Determines if a specified value is not in a collection</span></span>       |
| `-Replace`     | <span data-ttu-id="d11e0-167">Ersetzt den angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="d11e0-167">Replaces the specified value</span></span>                                 |

<span data-ttu-id="d11e0-168">Bei allen in Tabelle 5-1 aufgelisteten Operatoren wird die Groß-/Kleinschreibung nicht beachtet.</span><span class="sxs-lookup"><span data-stu-id="d11e0-168">All of the operators listed in Table 5-1 are case-insensitive.</span></span> <span data-ttu-id="d11e0-169">Stellen Sie dem in Tabelle 5-1 aufgelisteten Operator ein `c` voran, damit die Groß-/Kleinschreibung beachtet wird.</span><span class="sxs-lookup"><span data-stu-id="d11e0-169">Place a `c` in front of the operator listed in Table 5-1 to make it case-sensitive.</span></span> <span data-ttu-id="d11e0-170">Beispielsweise ist `-ceq` die Version des Vergleichsoperators `-eq`, bei der die Groß-/Kleinschreibung beachtet wird.</span><span class="sxs-lookup"><span data-stu-id="d11e0-170">For example, `-ceq` is the case-sensitive version of the `-eq` comparison operator.</span></span>

<span data-ttu-id="d11e0-171">„PowerShell“ in gemischter Schreibweise ist gleich der Variante in Kleinbuchstaben „powershell“, wenn der Vergleichsoperator „ gleich“ verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d11e0-171">Proper case "PowerShell" is equal to lower case "powershell" using the equals comparison operator.</span></span>

```powershell
'PowerShell' -eq 'powershell'
```

```Output
True
```

<span data-ttu-id="d11e0-172">Es ist nicht gleich, wenn die Variante des Vergleichsoperators „gleich“ mit Beachtung der Groß-/Kleinschreibung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d11e0-172">It's not equal using the case-sensitive version of the equals comparison operator.</span></span>

```powershell
'PowerShell' -ceq 'powershell'
```

```Output
False
```

<span data-ttu-id="d11e0-173">Der Vergleichsoperator „ungleich“ kehrt die Bedingung um.</span><span class="sxs-lookup"><span data-stu-id="d11e0-173">The not equal comparison operator reverses the condition.</span></span>

```powershell
'PowerShell' -ne 'powershell'
```

```Output
False
```

<span data-ttu-id="d11e0-174">„Größer als“, „Größer als oder gleich“, „Kleiner als“ und „Kleiner als oder gleich“ funktionieren alle mit Zeichenfolgen- und mit Zahlenwerten.</span><span class="sxs-lookup"><span data-stu-id="d11e0-174">Greater than, greater than or equal to, less than, and less than or equal all work with string or numeric values.</span></span>

```powershell
5 -gt 5
```

```Output
False
```

<span data-ttu-id="d11e0-175">Die Verwendung von „Größer als oder gleich“ anstelle von „Größer als“ im vorherigen Beispiel gibt den **booleschen Wert** „true“ zurück, da fünf gleich fünf ist.</span><span class="sxs-lookup"><span data-stu-id="d11e0-175">Using greater than or equal to instead of greater than with the previous example returns the **Boolean** true since five is equal to five.</span></span>

```powershell
5 -ge 5
```

```Output
True
```

<span data-ttu-id="d11e0-176">Basierend auf den Ergebnissen der beiden vorherigen Beispiele können Sie wahrscheinlich erraten, wie die Operatoren „Kleiner als“ und „Kleiner als oder gleich“ funktionieren.</span><span class="sxs-lookup"><span data-stu-id="d11e0-176">Based on the results from the previous two examples, you can probably guess how both less than and less than or equal to work.</span></span>

```powershell
5 -lt 10
```

```Output
True
```

<span data-ttu-id="d11e0-177">Die Operatoren `-Like` und `-Match` können verwirrend sein, selbst für erfahrene PowerShell-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="d11e0-177">The `-Like` and `-Match` operators can be confusing, even for experienced PowerShell users.</span></span> <span data-ttu-id="d11e0-178">`-Like` wird mit den Platzhalterzeichen `*` und `?` verwendet, um „wie“-Vergleiche auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-178">`-Like` is used with wildcard the characters `*` and `?` to perform "like" matches.</span></span>

```powershell
'PowerShell' -like '*shell'
```

```Output
True
```

<span data-ttu-id="d11e0-179">`-Match` verwendet einen regulären Ausdruck, um den Vergleich durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-179">`-Match` uses a regular expression to perform the matching.</span></span>

```powershell
'PowerShell' -match '^*.shell$'
```

```Output
True
```

<span data-ttu-id="d11e0-180">Verwenden Sie den Bereichsoperator (range), um die Zahlen 1 bis 10 in einer Variablen zu speichern.</span><span class="sxs-lookup"><span data-stu-id="d11e0-180">Use the range operator to store the numbers 1 through 10 in a variable.</span></span>

```powershell
$Numbers = 1..10
```

```Output
```

<span data-ttu-id="d11e0-181">Bestimmen Sie, ob die Variable `$Numbers` 15 enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-181">Determine if the `$Numbers` variable includes 15.</span></span>

```powershell
$Numbers -contains 15
```

```Output
False
```

<span data-ttu-id="d11e0-182">Bestimmen Sie, ob sie die Zahl 10 enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-182">Determine if it includes the number 10.</span></span>

```powershell
$Numbers -contains 10
```

```Output
True
```

<span data-ttu-id="d11e0-183">`-NotContains` kehrt die Logik um, um festzustellen, ob die `$Numbers` Variable einen Wert nicht enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-183">`-NotContains` reverses the logic to see if the `$Numbers` variable doesn't contain a value.</span></span>

```powershell
$Numbers -notcontains 15
```

```Output
True
```

<span data-ttu-id="d11e0-184">Im vorherigen Beispiel wird der **boolesche Wert** „true“ zurückgegeben, da es zutrifft, dass die Variable `$Numbers` 15 nicht enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-184">The previous example returns the **Boolean** true because it's true that the `$Numbers` variable doesn't contain 15.</span></span> <span data-ttu-id="d11e0-185">Sie enthält jedoch die Zahl 10, sodass beim Testen das Ergebnis „false“ ist.</span><span class="sxs-lookup"><span data-stu-id="d11e0-185">It does however contain the number 10 so it's false when it's tested.</span></span>

```powershell
$Numbers -notcontains 10
```

```Output
False
```

<span data-ttu-id="d11e0-186">Der Vergleichsoperator „in“ wurde erstmals in PowerShell-Version 3.0 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="d11e0-186">The "in" comparison operator was first introduced in PowerShell version 3.0.</span></span> <span data-ttu-id="d11e0-187">Er wird verwendet, um zu bestimmen, ob sich ein Wert in einem Array befindet.</span><span class="sxs-lookup"><span data-stu-id="d11e0-187">It's used to determine if a value is "in" an array.</span></span> <span data-ttu-id="d11e0-188">Die Variable `$Numbers` ist ein Array, da sie mehrere Werte enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-188">The `$Numbers` variable is an array since it contains multiple values.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="d11e0-189">Mit anderen Worten: `-in` führt denselben Test wie der Vergleichsoperator „enthält“ (contains) aus, mit der Ausnahme, dass er von der entgegengesetzten Richtung aus arbeitet.</span><span class="sxs-lookup"><span data-stu-id="d11e0-189">In other words, `-in` performs the same test as the contains comparison operator except from the opposite direction.</span></span>

```powershell
10 -in $Numbers
```

```Output
True
```

<span data-ttu-id="d11e0-190">15 befindet sich nicht im Array `$Numbers`, weshalb im folgenden Beispiel „false“ zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d11e0-190">15 isn't in the `$Numbers` array so false is returned in the following example.</span></span>

```powershell
15 -in $Numbers
```

```Output
False
```

<span data-ttu-id="d11e0-191">Ebenso wie der Operator `-contains`, kehrt `not` die Logik für den Operator `-in` um.</span><span class="sxs-lookup"><span data-stu-id="d11e0-191">Just like the `-contains` operator, `not` reverses the logic for the `-in` operator.</span></span>

```powershell
10 -notin $Numbers
```

```Output
False
```

<span data-ttu-id="d11e0-192">Im vorherigen Beispiel wird „false“ zurückgegeben, weil das Array `$Numbers` 10 enthält und die Bedingung in einem Test bestand, um zu ermitteln, ob es 10 nicht enthält.</span><span class="sxs-lookup"><span data-stu-id="d11e0-192">The previous example returns false because the `$Numbers` array does include 10 and the condition was testing to determine if it didn't contain 10.</span></span>

<span data-ttu-id="d11e0-193">15 befindet sich „nicht in“ dem Array `$Numbers`, weshalb der **boolesche Wert** „true“ zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d11e0-193">15 is "not in" the `$Numbers` array so it returns the **Boolean** true.</span></span>

```powershell
15 -notin $Numbers
```

```Output
True
```

<span data-ttu-id="d11e0-194">Der Operator `-replace` macht genau das, woran Sie denken.</span><span class="sxs-lookup"><span data-stu-id="d11e0-194">The `-replace` operator does just want you would think.</span></span> <span data-ttu-id="d11e0-195">Er wird verwendet, um etwas zu ersetzen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-195">It's used to replace something.</span></span> <span data-ttu-id="d11e0-196">Wenn Sie nur einen Wert angeben, wird dieser Wert durch nichts ersetzt.</span><span class="sxs-lookup"><span data-stu-id="d11e0-196">Specifying one value replaces that value with nothing.</span></span> <span data-ttu-id="d11e0-197">Im folgenden Beispiel wird „Shell“ durch nichts ersetzt.</span><span class="sxs-lookup"><span data-stu-id="d11e0-197">In the following example, I replace "Shell" with nothing.</span></span>

```powershell
'PowerShell' -replace 'Shell'
```

```Output
Power
```

<span data-ttu-id="d11e0-198">Wenn Sie einen Wert durch einen anderen Wert ersetzen möchten, geben Sie den neuen Wert hinter dem Muster an, das Sie ersetzen möchten.</span><span class="sxs-lookup"><span data-stu-id="d11e0-198">If you want to replace a value with a different value, specify the new value after the pattern you want to replace.</span></span> <span data-ttu-id="d11e0-199">„SQL Saturday in Baton Rouge“ ist ein Ereignis, bei dem ich jedes Jahr versuche, zu sprechen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-199">SQL Saturday in Baton Rouge is an event that I try to speak at every year.</span></span> <span data-ttu-id="d11e0-200">Im folgenden Beispiel ersetze ich das Wort „Saturday“ durch die Abkürzung „Sat“.</span><span class="sxs-lookup"><span data-stu-id="d11e0-200">In the following example, I replace the word "Saturday" with the abbreviation "Sat".</span></span>

```powershell
'SQL Saturday - Baton Rouge' -Replace 'saturday','Sat'
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="d11e0-201">Es gibt auch Methoden wie **Replace()** , die zum Ersetzen von Elementen verwendet werden können, die der Art und Weise ähneln, wie der replace-Operator funktioniert.</span><span class="sxs-lookup"><span data-stu-id="d11e0-201">There are also methods like **Replace()** that can be used to replace things similar to the way the replace operator works.</span></span> <span data-ttu-id="d11e0-202">Der Operator `-Replace` beachtet jedoch standardmäßig nicht die Groß-und Kleinschreibung, die **Replace()** -Methode hingegen berücksichtigt die Groß-/Kleinschreibung.</span><span class="sxs-lookup"><span data-stu-id="d11e0-202">However, the `-Replace` operator is case-insensitive by default, and the **Replace()** method is case-sensitive.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('saturday','Sat')
```

```Output
SQL Saturday - Baton Rouge
```

<span data-ttu-id="d11e0-203">Beachten Sie, dass das Wort „Saturday“ im vorherigen Beispiel nicht ersetzt wurde.</span><span class="sxs-lookup"><span data-stu-id="d11e0-203">Notice that the word "Saturday" wasn't replaced in the previous example.</span></span> <span data-ttu-id="d11e0-204">Dies liegt daran, dass es mit anderer Groß-/Kleinschreibung als das Original angegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="d11e0-204">This is because it was specified in a different case than the original.</span></span> <span data-ttu-id="d11e0-205">Wenn das Wort „Saturday“ in derselben Groß-/Kleinschreibung wie das Original angegeben wird, ersetzt die **Replace()** -Methode es wie erwartet.</span><span class="sxs-lookup"><span data-stu-id="d11e0-205">When the word "Saturday" is specified in the same case as the original, the **Replace()** method does replace it as expected.</span></span>

```powershell
'SQL Saturday - Baton Rouge'.Replace('Saturday','Sat')
```

```Output
SQL Sat - Baton Rouge
```

<span data-ttu-id="d11e0-206">Gehen Sie bei der Verwendung von Methoden zum Transformieren von Daten vorsichtig vor, da Sie auf unvorhergesehene Probleme stoßen können, z. B. das Nichtbestehen des _Turkey-Tests_.</span><span class="sxs-lookup"><span data-stu-id="d11e0-206">Be careful when using methods to transform data because you can run into unforeseen problems, such as failing the _Turkey Test_.</span></span> <span data-ttu-id="d11e0-207">Ein Beispiel finden Sie in dem Blogartikel [Verwenden von Pester zum Testen von PowerShell-Code mit anderen Kulturen][].</span><span class="sxs-lookup"><span data-stu-id="d11e0-207">For an example, see the blog article titled [Using Pester to Test PowerShell Code with Other Cultures][].</span></span> <span data-ttu-id="d11e0-208">Meine Empfehlung ist es, einen Operator anstelle einer Methode zu verwenden, wenn dies möglich ist, um diese Art von Problemen zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="d11e0-208">My recommendation is to use an operator instead of a method whenever possible to avoid these types of problems.</span></span>

<span data-ttu-id="d11e0-209">Obwohl die Vergleichsoperatoren wie in den vorherigen Beispielen gezeigt verwendet werden können, verwende ich sie doch in der Regel mit dem Cmdlet `Where-Object`, um eine Art von Filterung durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="d11e0-209">While the comparison operators can be used as shown in the previous examples, I normally find myself using them with the `Where-Object` cmdlet to perform some type of filtering.</span></span>

## <a name="summary"></a><span data-ttu-id="d11e0-210">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="d11e0-210">Summary</span></span>

<span data-ttu-id="d11e0-211">In diesem Kapitel haben Sie eine Reihe unterschiedlicher Themen kennengelernt, nämlich „Rechts formatieren“, „Aliase“, „Anbieter“ und „Vergleichsoperatoren“.</span><span class="sxs-lookup"><span data-stu-id="d11e0-211">In this chapter, you've learned a number of different topics to include Formatting Right, Aliases, Providers, and Comparison Operators.</span></span>

## <a name="review"></a><span data-ttu-id="d11e0-212">Überprüfung</span><span class="sxs-lookup"><span data-stu-id="d11e0-212">Review</span></span>

1. <span data-ttu-id="d11e0-213">Warum ist es notwendig, die Formatierung so weit wie möglich rechts durchzuführen?</span><span class="sxs-lookup"><span data-stu-id="d11e0-213">Why is it necessary to perform Formatting as far to the right as possible?</span></span>
1. <span data-ttu-id="d11e0-214">Wie bestimmen Sie, wie das tatsächliche Cmdlet zum Alias `%` lautet?</span><span class="sxs-lookup"><span data-stu-id="d11e0-214">How do you determine what the actual cmdlet is for the `%` alias?</span></span>
1. <span data-ttu-id="d11e0-215">Warum sollten Sie keine Aliase in Skripts verwenden, die Sie speichern, oder in Code, den Sie mit anderen teilen?</span><span class="sxs-lookup"><span data-stu-id="d11e0-215">Why shouldn't you use aliases in scripts you save or code you share with others?</span></span>
1. <span data-ttu-id="d11e0-216">Führen Sie eine Verzeichnisauflistung auf den Laufwerken durch, die einem der Registrierungsanbieter zugeordnet sind.</span><span class="sxs-lookup"><span data-stu-id="d11e0-216">Perform a directory listing on the drives that are associated with one of the registry providers.</span></span>
1. <span data-ttu-id="d11e0-217">Was ist einer der Hauptvorteile bei der Verwendung des replace-Operators anstelle der Replace-Methode?</span><span class="sxs-lookup"><span data-stu-id="d11e0-217">What's one of the main benefits of using the replace operator instead of the replace method?</span></span>

## <a name="recommended-reading"></a><span data-ttu-id="d11e0-218">Empfohlene Lektüre</span><span class="sxs-lookup"><span data-stu-id="d11e0-218">Recommended Reading</span></span>

- <span data-ttu-id="d11e0-219">[Format-Table][]</span><span class="sxs-lookup"><span data-stu-id="d11e0-219">[Format-Table][]</span></span>
- <span data-ttu-id="d11e0-220">[Format-List][]</span><span class="sxs-lookup"><span data-stu-id="d11e0-220">[Format-List][]</span></span>
- <span data-ttu-id="d11e0-221">[Format-Wide][]</span><span class="sxs-lookup"><span data-stu-id="d11e0-221">[Format-Wide][]</span></span>
- <span data-ttu-id="d11e0-222">[about_Aliases][]</span><span class="sxs-lookup"><span data-stu-id="d11e0-222">[about_Aliases][]</span></span>
- <span data-ttu-id="d11e0-223">[about_Providers][]</span><span class="sxs-lookup"><span data-stu-id="d11e0-223">[about_Providers][]</span></span>
- <span data-ttu-id="d11e0-224">[about_Comparison_Operators][]</span><span class="sxs-lookup"><span data-stu-id="d11e0-224">[about_Comparison_Operators][]</span></span>
- <span data-ttu-id="d11e0-225">[about_Arrays][]</span><span class="sxs-lookup"><span data-stu-id="d11e0-225">[about_Arrays][]</span></span>

<!-- link references -->
[SMSS]: /sql/ssms/download-sql-server-management-studio-ssms
[Format-Table]: /powershell/module/microsoft.powershell.utility/format-table
[Format-List]: /powershell/module/microsoft.powershell.utility/format-list
[Format-Wide]: /powershell/module/microsoft.powershell.utility/format-wide
[about_Aliases]: /powershell/module/microsoft.powershell.core/about/about_aliases
[about_Providers]: /powershell/module/microsoft.powershell.core/about/about_providers
[about_Comparison_Operators]: /powershell/module/microsoft.powershell.core/about/about_comparison_operators
[about_Arrays]: /powershell/module/microsoft.powershell.core/about/about_arrays
[Verwenden von Pester zum Testen von PowerShell-Code mit anderen Kulturen]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/
[Using Pester to Test PowerShell Code with Other Cultures]: https://mikefrobbins.com/2015/10/22/using-pester-to-test-powershell-code-with-other-cultures/

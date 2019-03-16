---
title: Erstellen ein Cmdlet für den Zugriff auf einen Data Store | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea15e00e-20dc-4209-9e97-9ffd763e5d97
caps.latest.revision: 8
ms.openlocfilehash: 28d55874960f9a64b986204411d38319ef1d0da7
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059523"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Erstellen eines Cmdlet für den Zugriff auf einen Datenspeicher

Dieser Abschnitt beschreibt, wie Sie ein Cmdlet zu erstellen, die gespeicherte Daten über ein Windows PowerShell-Anbieter zugreift. Diese Art von Cmdlet verwendet die Windows PowerShell-Anbieter-Infrastruktur von der Windows PowerShell-Laufzeit und daher die Cmdlet-Klasse ableiten muss die [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Basisklasse.

Das Select-Str-Cmdlet, das hier beschriebene kann suchen und markieren Zeichenfolgen in einer Datei oder das Objekt. Die Muster, die mit dem die Zeichenfolge können explizit über angegeben werden, die `Path` Parameter des Cmdlets oder implizit über die `Script` Parameter.

Das Cmdlet alle Windows PowerShell-Anbieter verwenden, die abgeleitet soll [System.Management.Automation.Provider.Icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider). Beispielsweise kann das Cmdlet angeben, der FileSystem-Anbieter oder der Variable-Anbieter, der von Windows PowerShell bereitgestellt wird. Weitere Informationen AboutWindows PowerShell-Anbieter, finden Sie unter [Entwerfen Ihrer Windows PowerShell-Anbieter](../prog-guide/designing-your-windows-powershell-provider.md).

Die folgenden: Themen in diesem Abschnitt

- [Definieren die Cmdlet-Klasse](#Defining-the-Cmdlet-Class)

- [Definieren von Parametern für den Datenzugriff](#Declaring-the-Path-Parameter)

- [Eingabeverarbeitungsmethoden überschreiben](#Overriding-Input-Processing-Methods)

- [Zugreifen auf Inhalte](#Accessing-Content)

- [Codebeispiel](#Code-Sample)

- [Definieren von Objekttypen und Formatierung](#Declaring-Search-Support-Parameters)

- [Erstellen das Cmdlet](#Building-the-Cmdlet)

- [Testen das Cmdlet](#Testing-the-Cmdlet)

## <a name="defining-the-cmdlet-class"></a>Definieren die Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist immer benennen das Cmdlet und .NET implementiert die Klasse, mit dem-Cmdlet deklarieren. Dieses Cmdlet erkennt bestimmte Zeichenfolgen, von der hier gewählte Verb-Name ist "Select", definiert der [System.Management.Automation.Verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) Klasse. Der Namen der Nomen "Str" wird verwendet, da das Cmdlet auf Zeichenfolgen angewendet. Beachten Sie, dass der cmdletnamen Verb- und den Namen der Cmdlet-Klasse übernommen werden, in der folgenden Deklaration. Weitere Informationen zu zulässigen Cmdlet-Verben, finden Sie unter [Cmdlet Verbnamen](./approved-verbs-for-windows-powershell-commands.md).

Die Klasse .NET für dieses Cmdlet muss abgeleitet werden, aus der [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Basisklasse, da die Unterstützung von der Windows PowerShell-Laufzeit benötigt werden dort, um den Windows PowerShell-Anbieter verfügbar zu machen die Infrastruktur. Beachten Sie, die mit diesem Cmdlet auch wird verwenden, der die reguläre Ausdrücke von .NET Framework-Klassen wie z. B. [System.Text.Regularexpressions.Regex](/dotnet/api/System.Text.RegularExpressions.Regex).

Der folgende Code ist die Definition der Klasse für dieses Cmdlet Select-Str.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Dieses Cmdlet definiert einen Standardparameter, die festlegen, indem die `DefaultParameterSetName` -Attribut der Klassendeklaration Schlüsselwort. Der Standard-Parametersatz `PatternParameterSet` wird verwendet, wenn die `Script` Parameter nicht angegeben. Weitere Informationen zu diesem Parameter finden Sie unter den `Pattern` und `Script` Erläuterung der Parameter im folgenden Abschnitt.

## <a name="defining-parameters-for-data-access"></a>Definieren von Parametern für den Datenzugriff

Dieses Cmdlet definiert mehrere Parameter, mit denen den Benutzer zum Zugreifen auf und untersuchen die gespeicherte Daten. Diese Parameter umfassen eine `Path` Parameter, der den Speicherort des Datenspeichers, gibt eine `Pattern` -Parameter, der angibt, das entsprechende Muster, die verwendet werden, bei der Suche und andere Parameter, die unterstützen, wie die Suche ausgeführt wird.

> [!NOTE]
> Weitere Informationen zu den Grundlagen der Parameter definieren, finden Sie unter [Hinzufügen von Parametern, die Eingabe über die Befehlszeile](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Deklarieren Sie den Path-Parameter

Um den Datenspeicher zu suchen, muss dieses Cmdlet einen Windows PowerShell-Pfad verwenden, den Windows PowerShell-Anbieter zu identifizieren, der Zugriff auf den Data Store entwickelt wurde. Aus diesem Grund definiert eine `Path` Parameter vom Typ String-Array an den Speicherort des Anbieters.

```csharp
[Parameter(
           Position = 0,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
[Parameter(
           Position = 0,
           ParameterSetName = "PatternParameterSet",
           ValueFromPipeline = true,
           Mandatory = true)]
           [Alias("PSPath")]
public string[] Path
{
  get { return paths; }
  set { paths = value; }
}
private string[] paths;
```

Beachten Sie, dass dieser Parameter auf zwei verschiedene Parametersätze gehört und über einen Alias verfügt.

Zwei [System.Management.Automation.Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) Attribute zu deklarieren, die die `Path` Parameter gehört zu den `ScriptParameterSet` und `PatternParameterSet`. Weitere Informationen zu Parametersätze, finden Sie unter [Parametersätze hinzufügen zu einem Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

Die [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) Attribut deklariert eine `PSPath` alias für die `Path` Parameter. Deklarieren diesen Alias wird für Konsistenz mit anderen Cmdlets, die auf Windows PowerShell-Anbieter zugreifen, dringend empfohlen. Weitere Informationen AboutWindows PowerShell-Pfaden, finden Sie unter "PowerShell-Pfad-Konzepte" in [Funktionsweise von Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58).

### <a name="declaring-the-pattern-parameter"></a>Deklarieren der Pattern-Parameters

Um die Muster zu suchende anzugeben, mit diesem Cmdlet deklariert einen `Pattern` Parameter, der ein Array von Zeichenfolgen ist. Ein positives Ergebnis wird zurückgegeben, wenn mindestens eines der Muster im Datenspeicher gefunden werden. Beachten Sie, dass diese Muster in ein Array aus kompilierten regulären Ausdrücken oder ein Array von Platzhaltermustern für Literale Suchvorgänge verwendet kompiliert werden können.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "PatternParameterSet",
           Mandatory = true)]
public string[] Pattern
{
  get { return patterns; }
  set { patterns = value; }
}
private string[] patterns;
private Regex[] regexPattern;
private WildcardPattern[] wildcardPattern;
```

Wenn dieser Parameter angegeben wird, wird das Cmdlet verwendet den Standard-Parametersatz `PatternParameterSet`. In diesem Fall verwendet das Cmdlet die Muster, die hier angegebenen Zeichenfolgen auswählen. Im Gegensatz dazu die `Script` Parameter kann auch verwendet werden, um ein Skript angeben, die das Muster enthält. Die `Script` und `Pattern` Parameter definieren zwei separate Parametersätze, damit sie sich gegenseitig ausschließende sind.

### <a name="declaring-search-support-parameters"></a>Deklarieren Sie die Suchparameter-Unterstützung

Dieses Cmdlet definiert die folgenden Support-Parameter, die verwendet werden können, so ändern Sie die Suchfunktionen von das-Cmdlet.

Die `Script` Parameter gibt einen Skriptblock, der verwendet werden kann, um eine alternative Suchmechanismus für das Cmdlet bereitzustellen. Das Skript muss das Muster für den Abgleich verwendet enthalten und Zurückgeben einer [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) Objekt. Beachten Sie, dass dieser Parameter auch den unique-Parameter, der identifiziert die `ScriptParameterSet` Parametersatz. Wenn die Windows PowerShell-Laufzeit diesen Parameter erkennt, verwendet es nur die Parameter, die zu gehören die `ScriptParameterSet` Parametersatz.

```csharp
[Parameter(
           Position = 1,
           ParameterSetName = "ScriptParameterSet",
           Mandatory = true)]
public ScriptBlock Script
{
  set { script = value; }
  get { return script; }
}
ScriptBlock script;
```

Die `SimpleMatch` Parameter ist ein Switch-Parameter, der angibt, ob das Cmdlet explizit den Mustern entsprechen, wie sie bereitgestellt werden. Wenn der Benutzer den Parameter in der Befehlszeile angegeben (`true`), das Cmdlet verwendet die Muster, wie sie bereitgestellt werden. Wenn der Parameter nicht angegeben ist (`false`), mit dem-Cmdlet verwendet reguläre Ausdrücke. Der Standardwert für diesen Parameter ist `false`.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

Die `CaseSensitive` Parameter ist ein Switch-Parameter, der angibt, ob Groß-/ Kleinschreibung durchgeführt wird. Wenn der Benutzer den Parameter in der Befehlszeile angegeben (`true`), überprüft das Cmdlet für die Groß- und Kleinschreibung von Zeichen, die beim Vergleichen von Mustern. Wenn der Parameter nicht angegeben ist (`false`), mit dem-Cmdlet wird nicht zwischen Groß- und Kleinschreibung unterschieden. Beispielsweise würde "MyFile" und "Myfile" sowohl als positive Treffer zurückgegeben. Der Standardwert für diesen Parameter ist `false`.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

Die `Exclude` und `Include` Parameter identifiziert die Elemente, die explizit ausgeschlossen oder in der Suche enthalten sind. Standardmäßig sucht das Cmdlet alle Elemente im Datenspeicher. Allerdings um die vom Cmdlet durchgeführten Suche einzuschränken, können diese Parameter werden verwendet, um Elemente in die Suche einbezogen werden explizit anzugeben oder ausgelassen.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

```csharp
[Parameter]
[ValidateNotNullOrEmpty]
public string[] Include
{
  get
  {
    return includeStrings;
  }
  set
  {
    includeStrings = value;

    this.include = new WildcardPattern[includeStrings.Length];
    for (int i = 0; i < includeStrings.Length; i++)
    {
      this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
    }
  }
}

internal string[] includeStrings = null;
internal WildcardPattern[] include = null;
```

### <a name="declaring-parameter-sets"></a>Deklarieren von Parametersätzen

Dieses Cmdlet verwendet zwei Parametersätze (`ScriptParameterSet` und `PatternParameterSet`, dies ist die Standardeinstellung) als Namen von zwei Parametersätze, die in den Datenzugriff verwendet. `PatternParameterSet` der Standard-Parameter festgelegt ist, und wird verwendet, wenn die `Pattern` Parameter angegeben ist. `ScriptParameterSet` wird verwendet, wenn der Benutzer über eine alternative Suchmechanismus gibt an, die `Script` Parameter. Weitere Informationen zu Parametersätze, finden Sie unter [Parametersätze hinzufügen zu einem Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Eingabeverarbeitungsmethoden überschreiben

Cmdlets müssen mindestens eine der Methoden zum Verarbeiten von Eingabe überschreiben die [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse. Weitere Informationen zu den Methoden für die Verarbeitung von Benutzereingaben, finden Sie unter [Erstellen Ihrer ersten Cmdlet](./creating-a-cmdlet-without-parameters.md).

Dieses Cmdlet aus, überschreibt die [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) Methode erstellen Sie ein Array von kompilierte reguläre Ausdrücke, die beim Start. Dies verbessert die Leistung bei Suchvorgängen, die keine einfache gleichheitsprüfung verwenden.

```csharp
protected override void BeginProcessing()
{
  WriteDebug("Validating patterns.");
  if (patterns != null)
  {
    foreach(string pattern in patterns)
    {
      if (pattern == null)
      ThrowTerminatingError(new ErrorRecord(
                            new ArgumentNullException(
                            "Search pattern cannot be null."),
                            "NullSearchPattern",
                            ErrorCategory.InvalidArgument,
                            pattern)
                            );
    }

    WriteVerbose("Search pattern(s) are valid.");

    // If a simple match is not specified, then
    // compile the regular expressions once.
    if (!simpleMatch)
    {
      WriteDebug("Compiling search regular expressions.");

      RegexOptions regexOptions = RegexOptions.Compiled;
      if (!caseSensitive)
         regexOptions |= RegexOptions.Compiled;
      regexPattern = new Regex[patterns.Length];

      for (int i = 0; i < patterns.Length; i++)
      {
        try
        {
          regexPattern[i] = new Regex(patterns[i], regexOptions);
        }
        catch (ArgumentException ex)
        {
          ThrowTerminatingError(new ErrorRecord(
                        ex,
                        "InvalidRegularExpression",
                        ErrorCategory.InvalidArgument,
                        patterns[i]
                     ));
        }
      } //Loop through patterns to create RegEx objects.

      WriteVerbose("Pattern(s) compiled into regular expressions.");
    }// If not a simple match.

    // If a simple match is specified, then compile the
    // wildcard patterns once.
    else
    {
      WriteDebug("Compiling search wildcards.");

      WildcardOptions wildcardOptions = WildcardOptions.Compiled;

      if (!caseSensitive)
      {
        wildcardOptions |= WildcardOptions.IgnoreCase;
      }

      wildcardPattern = new WildcardPattern[patterns.Length];
      for (int i = 0; i < patterns.Length; i++)
      {
        wildcardPattern[i] =
                     new WildcardPattern(patterns[i], wildcardOptions);
      }

      WriteVerbose("Pattern(s) compiled into wildcard expressions.");
    }// If match is a simple match.
  }// If valid patterns are available.
}// End of function BeginProcessing().
```

Dieses Cmdlet überschreibt auch die [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode, um die Auswahl der Zeichenfolge zu verarbeiten, die der Benutzer in der Befehlszeile angegeben wird. Schreibt die Ergebnisse der Auswahl der Zeichenfolge in Form eines benutzerdefinierten Objekts durch Aufrufen einer privates **MatchString** Methode.

```csharp
protected override void ProcessRecord()
{
  UInt64 lineNumber = 0;
  MatchInfo result;
  ArrayList nonMatches = new ArrayList();

  // Walk the list of paths and search the contents for
  // any of the specified patterns.
  foreach (string psPath in paths)
  {
    // Once the filepaths are expanded, we may have more than one
    // path, so process all referenced paths.
    foreach(PathInfo path in
            SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
           )
    {
      WriteVerbose("Processing path " + path.Path);

      // Check if the path represents one of the items to be
      // excluded. If so, continue to next path.
      if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
         continue;

      // Get the content reader for the item(s) at the
      // specified path.
      Collection<IContentReader> readerCollection = null;
      try
      {
        readerCollection =
                    this.InvokeProvider.Content.GetReader(path.Path);
      }
      catch (PSNotSupportedException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "ContentAccessNotSupported",
                    ErrorCategory.NotImplemented,
                    path.Path)
                   );
        return;
      }

      foreach(IContentReader reader in readerCollection)
      {
        // Reset the line number for this path.
        lineNumber = 0;

        // Read in a single block (line in case of a file)
        // from the object.
        IList items = reader.Read(1);

        // Read and process one block(line) at a time until
        // no more blocks(lines) exist.
        while (items != null && items.Count == 1)
        {
          // Increment the line number each time a line is
          // processed.
          lineNumber++;

          String message = String.Format("Testing line {0} : {1}",
                                        lineNumber, items[0]);

          WriteDebug(message);

          result = SelectString(items[0]);

          if (result != null)
          {
            result.Path = path.Path;
            result.LineNumber = lineNumber;

            WriteObject(result);
          }
          else
          {
            // Add the block(line) that did not match to the
            // collection of non matches , which will be stored
            // in the SessionState variable $NonMatches
            nonMatches.Add(items[0]);
          }

          // Get the next line from the object.
          items = reader.Read(1);

        }// While loop for reading one line at a time.
      }// Foreach loop for reader collection.
    }// Foreach loop for processing referenced paths.
  }// Foreach loop for walking of path list.

  // Store the list of non-matches in the
  // session state variable $NonMatches.
  try
  {
    this.SessionState.PSVariable.Set("NonMatches", nonMatches);
  }
  catch (SessionStateUnauthorizedAccessException ex)
  {
    WriteError(new ErrorRecord(ex,
               "CannotWriteVariableNonMatches",
               ErrorCategory.InvalidOperation,
               nonMatches)
              );
  }

}// End of protected override void ProcessRecord().
```

## <a name="accessing-content"></a>Zugreifen auf Inhalte

Ihr Cmdlet muss öffnen, den Anbieter, die von der Windows PowerShell-Pfad angegeben ist, damit sie die Daten zugreifen kann. Die [System.Management.Automation.Sessionstate](/dotnet/api/System.Management.Automation.SessionState) Objekt für der Runspace für den Zugriff auf den Anbieter verwendet wird, während er sich die [System.Management.Automation.PSCmdlet.Invokeprovider*](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) Eigenschaft der Cmdlet wird verwendet, um den Anbieter zu öffnen. Zugriff auf Inhalt wird bereitgestellt, durch Abrufen der [System.Management.Automation.Providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) -Objekt für den Anbieter geöffnet.

Dieses Beispiel-Select-Str-Cmdlet verwendet die [System.Management.Automation.Providerintrinsics.Content*](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) Eigenschaft, um den Inhalt überprüft verfügbar zu machen. Sie können dann aufrufen, die [System.Management.Automation.Contentcmdletproviderintrinsics.Getreader*](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) -Methode und übergeben den erforderlichen Windows PowerShell-Pfad.

## <a name="code-sample"></a>Codebeispiel

Der folgende Code zeigt die Implementierung dieser Version von dieser Select-Str-Cmdlet. Beachten Sie, dass dieser Code die Cmdlet-Klasse, private Methoden, die vom Cmdlet verwendet und der Windows PowerShell-Snap-in-Code verwendet, um das Cmdlet zu registrieren. Weitere Informationen zum Registrieren des Cmdlets, finden Sie unter [erstellen das Cmdlet](#Building-the-Cmdlet).

```csharp
//
// Copyright (c) 2006 Microsoft Corporation. All rights reserved.
//
// THIS CODE AND INFORMATION IS PROVIDED "AS IS" WITHOUT WARRANTY OF
// ANY KIND, EITHER EXPRESSED OR IMPLIED, INCLUDING BUT NOT LIMITED TO
// THE IMPLIED WARRANTIES OF MERCHANTABILITY AND/OR FITNESS FOR A
// PARTICULAR PURPOSE.
//
using System;
using System.Text.RegularExpressions;
using System.Collections;
using System.Collections.ObjectModel;
using System.Management.Automation;
using System.Management.Automation.Provider;
using System.ComponentModel;

namespace Microsoft.Samples.PowerShell.Commands
{
  #region SelectStringCommand
  /// <summary>
  /// This cmdlet searches through PSObjects for particular patterns.
  /// </summary>
  /// <remarks>
  /// This cmdlet can be used to search any object, such as a file or a
  /// variable, whose provider exposes methods for reading and writing
  /// content.
  /// </remarks>
  [Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
  public class SelectStringCommand : PSCmdlet
  {
    #region Parameters
    /// <summary>
    /// Declare a Path parameter that specifies where the data is stored.
    /// This parameter must specify a PowerShell that indicates the
    /// PowerShell provider that is used to access the objects to be
    /// searched for matching patterns. This parameter should also have
    /// a PSPath alias to provide consistency with other cmdlets that use
    /// PowerShell providers.
    /// </summary>
    /// <value>Path of the object(s) to search.</value>
    [Parameter(
               Position = 0,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    [Parameter(
               Position = 0,
               ParameterSetName = "PatternParameterSet",
               ValueFromPipeline = true,
               Mandatory = true)]
               [Alias("PSPath")]
    public string[] Path
    {
      get { return paths; }
      set { paths = value; }
    }
    private string[] paths;

    /// <summary>
    /// Declare a Pattern parameter that specifies the pattern(s)
    /// used to find matching patterns in the string representation
    /// of the objects. A positive result will be returned
    /// if any of the patterns are found in the objects.
    /// </summary>
    /// <remarks>
    /// The patterns will be compiled into an array of wildcard
    /// patterns for a simple match (literal string matching),
    /// or the patterns will be converted into an array of compiled
    /// regular expressions.
    /// </remarks>
    /// <value>Array of patterns to search.</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "PatternParameterSet",
               Mandatory = true)]
    public string[] Pattern
    {
      get { return patterns; }
      set { patterns = value; }
    }
    private string[] patterns;
    private Regex[] regexPattern;
    private WildcardPattern[] wildcardPattern;

    /// <summary>
    /// Declare a Script parameter that specifies a script block
    /// that is called to perform the matching operations
    /// instead of the matching performed by the cmdlet.
    /// </summary>
    /// <value>Script block that will be called for matching</value>
    [Parameter(
               Position = 1,
               ParameterSetName = "ScriptParameterSet",
               Mandatory = true)]
    public ScriptBlock Script
    {
      set { script = value; }
      get { return script; }
    }
    ScriptBlock script;

    /// <summary>
    /// Declare a switch parameter that specifies if the pattern(s) are used
    /// literally. If not (default), searching is
    /// done using regular expressions.
    /// </summary>
    /// <value>If True, a literal pattern is used.</value>
    [Parameter]
    public SwitchParameter SimpleMatch
    {
      get { return simpleMatch; }
      set { simpleMatch = value; }
    }
    private bool simpleMatch;

    /// <summary>
    /// Declare a switch parameter that specifies if a case-sensitive
    /// search is performed.  If not (default), a case-insensitive search
    /// is performed.
    /// </summary>
    /// <value>If True, a case-sensitive search is made.</value>
    [Parameter]
    public SwitchParameter CaseSensitive
    {
      get { return caseSensitive; }
      set { caseSensitive = value; }
    }
    private bool caseSensitive;

    /// <summary>
    /// Declare an Include parameter that species which
    /// specific items are searched.  When this parameter
    /// is used, items that are not listed here are omitted
    /// from the search.
    /// </summary>
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Include
    {
      get
      {
        return includeStrings;
      }
      set
      {
        includeStrings = value;

        this.include = new WildcardPattern[includeStrings.Length];
        for (int i = 0; i < includeStrings.Length; i++)
        {
          this.include[i] = new WildcardPattern(includeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }

    internal string[] includeStrings = null;
    internal WildcardPattern[] include = null;

    /// <summary>
    /// Declare an Exclude parameter that species which
    /// specific items are omitted from the search.
    /// </summary>
    ///
    [Parameter]
    [ValidateNotNullOrEmpty]
    public string[] Exclude
    {
      get
      {
        return excludeStrings;
      }
      set
      {
        excludeStrings = value;

        this.exclude = new WildcardPattern[excludeStrings.Length];
        for (int i = 0; i < excludeStrings.Length; i++)
        {
          this.exclude[i] = new WildcardPattern(excludeStrings[i], WildcardOptions.IgnoreCase);
        }
      }
    }
    internal string[] excludeStrings;
    internal WildcardPattern[] exclude;

    #endregion Parameters

    #region Overrides
    /// <summary>
    /// If regular expressions are used for pattern matching,
    /// then build an array of compiled regular expressions
    /// at startup. This increases performance during scanning
    /// operations when simple matching is not used.
    /// </summary>
    protected override void BeginProcessing()
    {
      WriteDebug("Validating patterns.");
      if (patterns != null)
      {
        foreach(string pattern in patterns)
        {
          if (pattern == null)
          ThrowTerminatingError(new ErrorRecord(
                                new ArgumentNullException(
                                "Search pattern cannot be null."),
                                "NullSearchPattern",
                                ErrorCategory.InvalidArgument,
                                pattern)
                                );
        }

        WriteVerbose("Search pattern(s) are valid.");

        // If a simple match is not specified, then
        // compile the regular expressions once.
        if (!simpleMatch)
        {
          WriteDebug("Compiling search regular expressions.");

          RegexOptions regexOptions = RegexOptions.Compiled;
          if (!caseSensitive)
             regexOptions |= RegexOptions.Compiled;
          regexPattern = new Regex[patterns.Length];

          for (int i = 0; i < patterns.Length; i++)
          {
            try
            {
              regexPattern[i] = new Regex(patterns[i], regexOptions);
            }
            catch (ArgumentException ex)
            {
              ThrowTerminatingError(new ErrorRecord(
                            ex,
                            "InvalidRegularExpression",
                            ErrorCategory.InvalidArgument,
                            patterns[i]
                         ));
            }
          } //Loop through patterns to create RegEx objects.

          WriteVerbose("Pattern(s) compiled into regular expressions.");
        }// If not a simple match.

        // If a simple match is specified, then compile the
        // wildcard patterns once.
        else
        {
          WriteDebug("Compiling search wildcards.");

          WildcardOptions wildcardOptions = WildcardOptions.Compiled;

          if (!caseSensitive)
          {
            wildcardOptions |= WildcardOptions.IgnoreCase;
          }

          wildcardPattern = new WildcardPattern[patterns.Length];
          for (int i = 0; i < patterns.Length; i++)
          {
            wildcardPattern[i] =
                         new WildcardPattern(patterns[i], wildcardOptions);
          }

          WriteVerbose("Pattern(s) compiled into wildcard expressions.");
        }// If match is a simple match.
      }// If valid patterns are available.
    }// End of function BeginProcessing().

    /// <summary>
    /// Process the input and search for the specified patterns.
    /// </summary>
    protected override void ProcessRecord()
    {
      UInt64 lineNumber = 0;
      MatchInfo result;
      ArrayList nonMatches = new ArrayList();

      // Walk the list of paths and search the contents for
      // any of the specified patterns.
      foreach (string psPath in paths)
      {
        // Once the filepaths are expanded, we may have more than one
        // path, so process all referenced paths.
        foreach(PathInfo path in
                SessionState.Path.GetResolvedPSPathFromPSPath(psPath)
               )
        {
          WriteVerbose("Processing path " + path.Path);

          // Check if the path represents one of the items to be
          // excluded. If so, continue to next path.
          if (!MeetsIncludeExcludeCriteria(path.ProviderPath))
             continue;

          // Get the content reader for the item(s) at the
          // specified path.
          Collection<IContentReader> readerCollection = null;
          try
          {
            readerCollection =
                        this.InvokeProvider.Content.GetReader(path.Path);
          }
          catch (PSNotSupportedException ex)
          {
            WriteError(new ErrorRecord(ex,
                       "ContentAccessNotSupported",
                        ErrorCategory.NotImplemented,
                        path.Path)
                       );
            return;
          }

          foreach(IContentReader reader in readerCollection)
          {
            // Reset the line number for this path.
            lineNumber = 0;

            // Read in a single block (line in case of a file)
            // from the object.
            IList items = reader.Read(1);

            // Read and process one block(line) at a time until
            // no more blocks(lines) exist.
            while (items != null && items.Count == 1)
            {
              // Increment the line number each time a line is
              // processed.
              lineNumber++;

              String message = String.Format("Testing line {0} : {1}",
                                            lineNumber, items[0]);

              WriteDebug(message);

              result = SelectString(items[0]);

              if (result != null)
              {
                result.Path = path.Path;
                result.LineNumber = lineNumber;

                WriteObject(result);
              }
              else
              {
                // Add the block(line) that did not match to the
                // collection of non matches , which will be stored
                // in the SessionState variable $NonMatches
                nonMatches.Add(items[0]);
              }

              // Get the next line from the object.
              items = reader.Read(1);

            }// While loop for reading one line at a time.
          }// Foreach loop for reader collection.
        }// Foreach loop for processing referenced paths.
      }// Foreach loop for walking of path list.

      // Store the list of non-matches in the
      // session state variable $NonMatches.
      try
      {
        this.SessionState.PSVariable.Set("NonMatches", nonMatches);
      }
      catch (SessionStateUnauthorizedAccessException ex)
      {
        WriteError(new ErrorRecord(ex,
                   "CannotWriteVariableNonMatches",
                   ErrorCategory.InvalidOperation,
                   nonMatches)
                  );
      }

    }// End of protected override void ProcessRecord().
    #endregion Overrides

    #region PrivateMethods
    /// <summary>
    /// Check for a match using the input string and the pattern(s)
    /// specified.
    /// </summary>
    /// <param name="input">The string to test.</param>
    /// <returns>MatchInfo object containing information about
    /// result of a match</returns>
    private MatchInfo SelectString(object input)
    {
      string line = null;

      try
      {
        // Convert the object to a string type
        // safely using language support methods
        line = (string)LanguagePrimitives.ConvertTo(
                                                    input,
                                                    typeof(string)
                                                    );
        line = line.Trim(' ','\t');
      }
      catch (PSInvalidCastException ex)
      {
        WriteError(new ErrorRecord(
                   ex,
                   "CannotCastObjectToString",
                   ErrorCategory.InvalidOperation,
                   input)
                   );

        return null;
      }

      MatchInfo result = null;

      // If a scriptblock has been specified, call it
      // with the path for processing.  It will return
      // one object.
      if (script != null)
      {
        WriteDebug("Executing script block.");

        Collection<PSObject> psObjects =
                             script.Invoke(
                                           line,
                                           simpleMatch,
                                           caseSensitive
                                          );

        foreach (PSObject psObject in psObjects)
        {
          if (LanguagePrimitives.IsTrue(psObject))
          {
            result = new MatchInfo();
            result.Line = line;
            result.IgnoreCase = !caseSensitive;

            break;
          } //End of If.
        } //End ForEach loop.
      } // End of If if script exists.

      // If script block exists, see if this line matches any
      // of the match patterns.
      else
      {
        int patternIndex = 0;

        while (patternIndex < patterns.Length)
        {
          if ((simpleMatch &&
              wildcardPattern[patternIndex].IsMatch(line))
              || (regexPattern != null
              && regexPattern[patternIndex].IsMatch(line))
             )
          {
            result = new MatchInfo();
            result.IgnoreCase = !caseSensitive;
            result.Line = line;
            result.Pattern = patterns[patternIndex];

            break;
          }

          patternIndex++;

        }// While loop through patterns.
      }// Else for no script block specified.

      return result;

    }// End of SelectString

    /// <summary>
    /// Check whether the supplied name meets the include/exclude criteria.
    /// That is - it's on the include list if the include list was
    /// specified, and not on the exclude list if the exclude list was specified.
    /// </summary>
    /// <param name="path">path to validate</param>
    /// <returns>True if the path is acceptable.</returns>
    private bool MeetsIncludeExcludeCriteria(string path)
    {
      bool ok = false;

      // See if the file is on the include list.
      if (this.include != null)
      {
        foreach (WildcardPattern patternItem in this.include)
        {
          if (patternItem.IsMatch(path))
          {
            ok = true;
            break;
          }
        }
      }
      else
      {
        ok = true;
      }

      if (!ok)
         return false;

      // See if the file is on the exclude list.
      if (this.exclude != null)
      {
        foreach (WildcardPattern patternItem in this.exclude)
        {
          if (patternItem.IsMatch(path))
          {
            ok = false;
            break;
          }
        }
      }

      return ok;
    } //MeetsIncludeExcludeCriteria
    #endregion Private Methods

  }// class SelectStringCommand

  #endregion SelectStringCommand

  #region MatchInfo

  /// <summary>
  /// Class representing the result of a pattern/literal match
  /// that is passed through the pipeline by the Select-Str cmdlet.
  /// </summary>
  public class MatchInfo
  {
    /// <summary>
    /// Indicates if the match was done ignoring case.
    /// </summary>
    /// <value>True if case was ignored.</value>
    public bool IgnoreCase
    {
      get { return ignoreCase; }
      set { ignoreCase = value; }
    }
    private bool ignoreCase;

    /// <summary>
    /// Specifies the number of the matching line.
    /// </summary>
    /// <value>The number of the matching line.</value>
    public UInt64 LineNumber
    {
      get { return lineNumber; }
      set { lineNumber = value; }
    }
    private UInt64 lineNumber;

    /// <summary>
    /// Specifies the text of the matching line.
    /// </summary>
    /// <value>The text of the matching line.</value>
    public string Line
    {
      get { return line; }
      set { line = value; }
    }
    private string line;

    /// <summary>
    /// Specifies the full path of the object(file) containing the
    /// matching line.
    /// </summary>
    /// <remarks>
    /// It will be "inputStream" if the object came from the input
    /// stream.
    /// </remarks>
    /// <value>The path name</value>
    public string Path
    {
      get { return path; }
      set
      {
        pathSet = true;
        path = value;
      }
    }
    private string path;
    private bool pathSet;

    /// <summary>
    /// Specifies the pattern that was used in the match.
    /// </summary>
    /// <value>The pattern string</value>
    public string Pattern
    {
      get { return pattern; }
      set { pattern = value; }
    }
    private string pattern;

    private const string MatchFormat = "{0}:{1}:{2}";

    /// <summary>
    /// Returns the string representation of this object. The format
    /// depends on whether a path has been set for this object or
    /// not.
    /// </summary>
    /// <remarks>
    /// If the path component is set, as would be the case when
    /// matching in a file, ToString() returns the path, line
    /// number and line text.  If path is not set, then just the
    /// line text is presented.
    /// </remarks>
    /// <returns>The string representation of the match object.</returns>
    public override string ToString()
    {
      if (pathSet)
         return String.Format(
         System.Threading.Thread.CurrentThread.CurrentCulture,
         MatchFormat,
         this.path,
         this.lineNumber,
         this.line
         );
      else
         return this.line;
    }
  }// End class MatchInfo

  #endregion

  #region PowerShell snap-in

  /// <summary>
  /// Create a PowerShell snap-in for the Select-Str cmdlet.
  /// </summary>
  [RunInstaller(true)]
  public class SelectStringPSSnapIn : PSSnapIn
  {
    /// <summary>
    /// Create an instance of the SelectStrPSSnapin class.
    /// </summary>
    public SelectStringPSSnapIn()
           : base()
    {
    }

    /// <summary>
    /// Specify the name of the PowerShell snap-in.
    /// </summary>
    public override string Name
    {
      get
      {
        return "SelectStrPSSnapIn";
      }
    }

    /// <summary>
    /// Specify the vendor of the PowerShell snap-in.
    /// </summary>
    public override string Vendor
    {
      get
      {
        return "Microsoft";
      }
    }

    /// <summary>
    /// Specify the localization resource information for the vendor.
    /// Use the format: SnapinName,VendorName.
    /// </summary>
    public override string VendorResource
    {
      get
      {
        return "SelectStrSnapIn,Microsoft";
      }
    }

    /// <summary>
    /// Specify the description of the PowerShell snap-in.
    /// </summary>
    public override string Description
    {
      get
        {
          return "This is a PowerShell snap-in for the Select-Str cmdlet.";
        }
    }

    /// <summary>
    /// Specify the localization resource information for the description.
    /// Use the format: SnapinName,Description.

    /// </summary>
    public override string DescriptionResource
    {
      get
      {
          return "SelectStrSnapIn,This is a PowerShell snap-in for the Select-Str cmdlet.";
      }
    }
  }
  #endregion PowerShell snap-in

} //namespace Microsoft.Samples.PowerShell.Commands;
```

## <a name="building-the-cmdlet"></a>Erstellen das Cmdlet

Nach der Implementierung eines Cmdlets, müssen Sie es mit Windows PowerShell über eine Windows PowerShell-Snap-in registrieren. Weitere Informationen zum Registrieren von Cmdlets finden Sie unter [wie zum Registrieren von Cmdlets, Anbietern und Hostanwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c).

## <a name="testing-the-cmdlet"></a>Testen das Cmdlet

Wenn Ihr Cmdlet in Windows PowerShell registriert wurde, können Sie es testen, indem Sie sie in der Befehlszeile ausführen. Das folgende Verfahren kann verwendet werden, um die Beispiel-Select-Str-Cmdlet testen.

1. Starten Sie Windows PowerShell, und suchen Sie die Anmerkungen zu dieser Datei für das Auftreten von Zeilen mit dem Ausdruck ".NET". Beachten Sie, dass der Anführungszeichen um den Namen des Pfads erforderlich sind, nur dann, wenn der Pfad besteht aus mehr als ein Wort an.

    ```powershell
    select-str -Path "notes" -Pattern ".NET" -SimpleMatch=$false
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    IgnoreCase   : True
    LineNumber   : 8
    Line         : Because Windows PowerShell works directly with .NET objects, there is often a .NET object
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    IgnoreCase   : True
    LineNumber   : 21
    Line         : You should normally define the class for a cmdlet in a .NET namespace
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : .NET
    ```

2. Suchen Sie die Anmerkungen zu dieser Datei für das Auftreten von Zeilen mit dem Wort "beendet", gefolgt von beliebigen anderen Text. Die `SimpleMatch` Parameter verwendet den Standardwert `false`. Bei der Suche Groß-/Kleinschreibung wird da die `CaseSensitive` Parametersatz zu `false`.

    ```powershell
    select-str -Path notes -Pattern "over*" -SimpleMatch -CaseSensitive:$false
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    IgnoreCase   : True
    LineNumber   : 45
    Line         : Override StopProcessing
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    IgnoreCase   : True
    LineNumber   : 49
    Line         : overriding the StopProcessing method
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : over*
    ```

3. Suchen Sie die Anmerkungen zu dieser Datei, die mit einem regulären Ausdruck als Muster. Das Cmdlet sucht nach alphabetische Zeichen und Leerzeichen in Klammern eingeschlossen.

    ```powershell
    select-str -Path notes -Pattern "\([A-Za-z:blank:]" -SimpleMatch:$false
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : Advisory Guidelines (Consider Following)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    IgnoreCase   : True
    LineNumber   : 53
    Line         : If your cmdlet has objects that are not disposed of (written to the pipeline)
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : \([A-Za-z:blank:]
    ```

4. Führen Sie nach Vorkommnissen des Worts "Parameter" Groß-/ Kleinschreibung der Anmerkungen zu dieser Datei ein.

    ```powershell
    select-str -Path notes -Pattern Parameter -CaseSensitive
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    IgnoreCase   : False
    LineNumber   : 6
    Line         : Support an InputObject Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    IgnoreCase   : False
    LineNumber   : 30
    Line         : Support Force Parameter
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\notes
    Pattern      : Parameter
    ```

5. Suchen Sie die Variable-Anbieter, die mit Windows PowerShell für Variablen, die numerische Werte von 0 bis 9 geliefert wird.

    ```powershell
    select-str -Path * -Pattern "[0-9]"
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    IgnoreCase   : True
    LineNumber   : 1
    Line         : 64
    Path         : Variable:\MaximumHistoryCount
    Pattern      : [0-9]
    ```

6. Verwenden Sie einen Skriptblock, um die Datei SelectStrCommandSample.cs für die Zeichenfolge "Bestellungen" suchen. Die **Cmatch** -Funktion für das Skript eine Musterübereinstimmung der Groß-/Kleinschreibung führt.

    ```powershell
    select-str -Path "SelectStrCommandSample.cs" -Script { if ($args[0] -cmatch "Pos"){ return $true } return $false }
    ```

    Die folgende Ausgabe wird angezeigt.

    ```output
    IgnoreCase   : True
    LineNumber   : 37
    Line         :    Position = 0.
    Path         : C:\PowerShell-Progs\workspace\Samples\SelectStr\SelectStrCommandSample.cs
    Pattern      :
    ```

## <a name="see-also"></a>Weitere Informationen

[Vorgehensweise: Erstellen eines Windows PowerShell-Cmdlets](https://msdn.microsoft.com/en-us/0d721742-c849-4d0d-964f-78ddd9cd258c)

[Erstellen eines ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erstellen ein Cmdlet, ändert das System](./creating-a-cmdlet-that-modifies-the-system.md)

[Entwerfen Sie Ihre Windows PowerShell-Anbieter](../prog-guide/designing-your-windows-powershell-provider.md)

[Funktionsweise von Windows PowerShell](https://msdn.microsoft.com/en-us/ced30e23-10af-4700-8933-49873bd84d58)

[So registrieren die Cmdlets, Anbieter, und Hosten von Anwendungen](https://msdn.microsoft.com/en-us/a41e9054-29c8-40ab-bf2b-8ce4e7ec1c8c)

[Windows PowerShell SDK](../windows-powershell-reference.md)

---
title: Erstellen eines Cmdlet für den Zugriff auf einen Datenspeicher
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 3096965ba9f99f70994f2fb5b180cc58691b04f8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74415697"
---
# <a name="creating-a-cmdlet-to-access-a-data-store"></a>Erstellen eines Cmdlet für den Zugriff auf einen Datenspeicher

In diesem Abschnitt wird beschrieben, wie Sie ein Cmdlet erstellen, das über einen Windows PowerShell-Anbieter auf gespeicherte Daten zugreift. Diese Art von Cmdlet verwendet die Windows PowerShell-Anbieter Infrastruktur der Windows PowerShell-Laufzeit. Daher muss die Cmdlet-Klasse von der Basisklasse " [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) " abgeleitet werden.

Das hier beschriebene Select-Str-Cmdlet kann Zeichen folgen in einer Datei oder einem Objekt suchen und auswählen. Die zum Identifizieren der Zeichenfolge verwendeten Muster können explizit über den `Path`-Parameter des Cmdlets oder implizit über den Parameter `Script` angegeben werden.

Das-Cmdlet ist für die Verwendung eines beliebigen Windows PowerShell-Anbieters konzipiert, der von [System. Management. Automation. Provider. icontentcmdletprovider](/dotnet/api/System.Management.Automation.Provider.IContentCmdletProvider)abgeleitet wird. Beispielsweise kann das Cmdlet den File System-Anbieter oder den Variablen Anbieter angeben, der von Windows PowerShell bereitgestellt wird. Weitere Informationen zu Windows PowerShell-Anbietern finden Sie unter [Entwerfen des Windows PowerShell-Anbieters](../prog-guide/designing-your-windows-powershell-provider.md).

## <a name="defining-the-cmdlet-class"></a>Definieren der Cmdlet-Klasse

Der erste Schritt bei der Cmdlet-Erstellung ist die Benennung des Cmdlets und das Deklarieren der .NET-Klasse, die das Cmdlet implementiert. Dieses Cmdlet erkennt bestimmte Zeichen folgen, sodass der hier gewählte Verb Name "Select" ist, der von der Klasse " [System. Management. Automation. verbscommon](/dotnet/api/System.Management.Automation.VerbsCommon) " definiert wird. Der Nomen Name "str" wird verwendet, da das Cmdlet auf Zeichen folgen anwendet. Beachten Sie in der folgenden Deklaration, dass das Cmdlet-Verb und der nominale Name in den Namen der Cmdlet-Klasse reflektiert werden. Weitere Informationen zu genehmigten Cmdlet-Verben finden Sie unter [Cmdlet-Verb Namen](./approved-verbs-for-windows-powershell-commands.md).

Die .NET-Klasse für dieses Cmdlet muss von der Basisklasse " [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) " abgeleitet werden, da Sie die von der Windows PowerShell-Laufzeit benötigte Unterstützung bereitstellt, um die Windows PowerShell-Anbieter Infrastruktur verfügbar zu machen. Beachten Sie, dass dieses Cmdlet auch die .NET Framework regulären Ausdrucks Klassen verwendet, wie z. b. [System. Text. RegularExpressions. Regex](/dotnet/api/System.Text.RegularExpressions.Regex).

Der folgende Code stellt die Klassendefinition für dieses SELECT-Str-Cmdlet dar.

```csharp
[Cmdlet(VerbsCommon.Select, "Str", DefaultParameterSetName="PatternParameterSet")]
public class SelectStringCommand : PSCmdlet
```

Dieses Cmdlet definiert einen Standardparameter Satz, indem der Klassen Deklaration das `DefaultParameterSetName` Attribute-Schlüsselwort hinzugefügt wird. Der Standardparameter Satz `PatternParameterSet` wird verwendet, wenn der `Script`-Parameter nicht angegeben wird. Weitere Informationen zu diesem Parametersatz finden Sie in der `Pattern`-und `Script` Parameter Diskussion im folgenden Abschnitt.

## <a name="defining-parameters-for-data-access"></a>Definieren von Parametern für den Datenzugriff

Dieses Cmdlet definiert mehrere Parameter, die es dem Benutzer ermöglichen, auf gespeicherte Daten zuzugreifen und diese zu überprüfen. Diese Parameter enthalten einen `Path` Parameter, der den Speicherort des Datenspeicher angibt, einen `Pattern` Parameter, der das in der Suche zu verwendende Muster angibt, und verschiedene weitere Parameter, die die Art der Suche unterstützen.

> [!NOTE]
> Weitere Informationen zu den Grundlagen der Definition von Parametern finden Sie unter [Hinzufügen von Parametern, die Befehlszeilen Eingaben verarbeiten](./adding-parameters-that-process-command-line-input.md).

### <a name="declaring-the-path-parameter"></a>Deklarieren des path-Parameters

Um den Datenspeicher zu finden, muss dieses Cmdlet einen Windows PowerShell-Pfad verwenden, um den Windows PowerShell-Anbieter zu identifizieren, der für den Zugriff auf den Datenspeicher konzipiert ist. Daher definiert Sie einen `Path` Parameter vom Typ Zeichen folgen Array, um den Speicherort des Anbieters anzugeben.

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

Beachten Sie, dass dieser Parameter zu zwei verschiedenen Parametersätzen gehört und über einen Alias verfügt.

Zwei [System. Management. Automation. Parameterattribute](/dotnet/api/System.Management.Automation.ParameterAttribute) -Attribute deklarieren, dass der `Path`-Parameter zum `ScriptParameterSet` und zum `PatternParameterSet`gehört. Weitere Informationen zu Parametersätzen finden Sie unter [Hinzufügen von Parametersätzen zu einem Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

Das [System. Management. Automation. Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) -Attribut deklariert einen `PSPath` Alias für den `Path`-Parameter. Das Deklarieren dieses Alias wird dringend empfohlen, um Konsistenz mit anderen Cmdlets zu erhalten, die auf Windows PowerShell-Anbieter zugreifen. Weitere Informationen zu Windows PowerShell-Pfaden finden Sie unter "PowerShell-Pfad Konzepte" unter [Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85)).

### <a name="declaring-the-pattern-parameter"></a>Deklarieren des pattern-Parameters

Um die zu suchenden Muster anzugeben, deklariert dieses Cmdlet einen `Pattern` Parameter, bei dem es sich um ein Array von Zeichen folgen handelt. Ein positives Ergebnis wird zurückgegeben, wenn eines der Muster im Datenspeicher gefunden wird. Beachten Sie, dass diese Muster in ein Array von kompilierten regulären Ausdrücken oder ein Array von Platzhalter Mustern kompiliert werden können, die für literalsuchvorgänge verwendet werden.

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

Wenn dieser Parameter angegeben wird, verwendet das Cmdlet den Standardparameter Satz `PatternParameterSet`. In diesem Fall verwendet das Cmdlet die hier angegebenen Muster, um Zeichen folgen auszuwählen. Im Gegensatz dazu kann der `Script`-Parameter auch verwendet werden, um ein Skript bereitzustellen, das die Muster enthält. Die Parameter "`Script`" und "`Pattern`" definieren zwei separate Parametersätze, sodass Sie sich gegenseitig ausschließen.

### <a name="declaring-search-support-parameters"></a>Deklarieren von Such Unterstützungs Parametern

Dieses Cmdlet definiert die folgenden Unterstützungs Parameter, die verwendet werden können, um die Suchfunktionen des Cmdlets zu ändern.

Der `Script`-Parameter gibt einen Skriptblock an, der zum Bereitstellen eines alternativen Suchmechanismus für das Cmdlet verwendet werden kann. Das Skript muss die Muster enthalten, die für die Übereinstimmung verwendet werden, und ein [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekt zurückgeben. Beachten Sie, dass dieser Parameter auch der eindeutige Parameter ist, der den `ScriptParameterSet` Parametersatz identifiziert. Wenn die Windows PowerShell-Laufzeit diesen Parameter sieht, werden nur Parameter verwendet, die zum `ScriptParameterSet` Parametersatz gehören.

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

Der `SimpleMatch`-Parameter ist ein Switch-Parameter, der angibt, ob das Cmdlet die Muster explizit mit den angegebenen Mustern vergleichen soll. Wenn der Benutzer den Parameter in der Befehlszeile (`true`) angibt, verwendet das Cmdlet die Muster, wenn Sie bereitgestellt werden. Wenn der-Parameter nicht angegeben wird (`false`), verwendet das Cmdlet reguläre Ausdrücke. Der Standardwert für diesen Parameter ist `false`.

```csharp
[Parameter]
public SwitchParameter SimpleMatch
{
  get { return simpleMatch; }
  set { simpleMatch = value; }
}
private bool simpleMatch;
```

Der `CaseSensitive` Parameter ist ein Switch-Parameter, der angibt, ob die Suche nach Groß-/Kleinschreibung durchgeführt wird. Wenn der Benutzer den Parameter in der Befehlszeile (`true`) angibt, überprüft das Cmdlet beim Vergleichen von Mustern das groß-und Kleinbuchstaben von Zeichen. Wenn der-Parameter nicht angegeben wird (`false`), unterscheidet das Cmdlet nicht zwischen Groß-und Kleinschreibung. Beispielsweise werden "MyFile" und "MyFile" als positive Treffer zurückgegeben. Der Standardwert für diesen Parameter ist `false`.

```csharp
[Parameter]
public SwitchParameter CaseSensitive
{
  get { return caseSensitive; }
  set { caseSensitive = value; }
}
private bool caseSensitive;
```

Mit den Parametern `Exclude` und `Include` werden Elemente identifiziert, die von der Suche explizit ausgeschlossen oder eingeschlossen werden. Standardmäßig durchsucht das Cmdlet alle Elemente im Datenspeicher. Um jedoch die durch das Cmdlet ausgeführte Suche einzuschränken, können diese Parameter verwendet werden, um explizit anzugeben, dass Elemente in die Suche eingeschlossen oder ausgelassen werden.

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

### <a name="declaring-parameter-sets"></a>Deklarieren von Parameter Sätzen

Dieses Cmdlet verwendet zwei Parametersätze (`ScriptParameterSet` und `PatternParameterSet`Standard) als die Namen von zwei Parametersätzen, die für den Datenzugriff verwendet werden. `PatternParameterSet` ist der Standardparameter Satz, der verwendet wird, wenn der `Pattern` Parameter angegeben wird. `ScriptParameterSet` wird verwendet, wenn der Benutzer mithilfe des Parameters `Script` einen alternativen Suchmechanismus angibt. Weitere Informationen zu Parametersätzen finden Sie unter [Hinzufügen von Parametersätzen zu einem Cmdlet](./adding-parameter-sets-to-a-cmdlet.md).

## <a name="overriding-input-processing-methods"></a>Überschreiben von Eingabe Verarbeitungsmethoden

Cmdlets müssen mindestens eine Eingabe Verarbeitungsmethode für die Klasse [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) überschreiben. Weitere Informationen zu den Eingabe Verarbeitungsmethoden finden Sie unter [Erstellen des ersten Cmdlets](./creating-a-cmdlet-without-parameters.md).

Mit diesem Cmdlet wird die [System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) -Methode überschrieben, um beim Start ein Array kompilierter regulärer Ausdrücke zu erstellen. Dies steigert die Leistung bei Such Vorgängen, die keine einfache Übereinstimmung verwenden.

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

Dieses Cmdlet überschreibt auch die [System. Management. Automation. Cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) -Methode, um die Zeichen folgen Auswahl zu verarbeiten, die der Benutzer in der Befehlszeile vornimmt. Die Ergebnisse der Zeichen folgen Auswahl werden in Form eines benutzerdefinierten Objekts geschrieben, indem eine private **matchstring** -Methode aufgerufen wird.

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

## <a name="accessing-content"></a>Zugreifen auf Inhalt

Ihr Cmdlet muss den Anbieter öffnen, der durch den Windows PowerShell-Pfad angegeben wird, sodass er auf die Daten zugreifen kann. Das [System. Management. Automation. SessionState](/dotnet/api/System.Management.Automation.SessionState) -Objekt für den Runspace wird für den Zugriff auf den Anbieter verwendet, während die [System. Management. Automation. PSCmdlet. invokeprovider *](/dotnet/api/System.Management.Automation.PSCmdlet.InvokeProvider) -Eigenschaft des Cmdlets zum Öffnen des Anbieters verwendet wird. Der Zugriff auf den Inhalt wird durch Abrufen des [System. Management. Automation. providerintrinsics](/dotnet/api/System.Management.Automation.ProviderIntrinsics) -Objekts für den geöffneten Anbieter bereitgestellt.

In diesem Beispiel Select-Str-Cmdlet wird die [System. Management. Automation. providerintrinsics. Content *](/dotnet/api/System.Management.Automation.ProviderIntrinsics.Content) -Eigenschaft verwendet, um den zu überprüfenden Inhalt verfügbar zu machen. Anschließend kann die [System. Management. Automation. contentcmdletproviderintrinsics. GetReader *](/dotnet/api/System.Management.Automation.ContentCmdletProviderIntrinsics.GetReader) -Methode aufgerufen werden, um den erforderlichen Windows PowerShell-Pfad zu übergeben.

## <a name="code-sample"></a>Codebeispiel

Der folgende Code zeigt die Implementierung dieser Version dieses SELECT-Str-Cmdlets. Beachten Sie, dass dieser Code die Cmdlet-Klasse, private Methoden, die vom Cmdlet verwendet werden, und den Windows PowerShell-Snap-in-Code enthält, der zum Registrieren des Cmdlets verwendet wird. Weitere Informationen zum Registrieren des Cmdlets finden Sie unter [Building the Cmdlet](#defining-the-cmdlet-class).

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

## <a name="building-the-cmdlet"></a>Cmdlet wird aufgebaut

Nachdem Sie ein Cmdlet implementiert haben, müssen Sie es über ein Windows PowerShell-Snap-in bei Windows PowerShell registrieren. Weitere Informationen zum Registrieren von Cmdlets finden [Sie unter Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85)).

## <a name="testing-the-cmdlet"></a>Testen des Cmdlets

Wenn das Cmdlet bei Windows PowerShell registriert wurde, können Sie es in der Befehlszeile testen. Das folgende Verfahren kann verwendet werden, um das Beispiel-"Select-Str"-Cmdlet zu testen.

1. Starten Sie Windows PowerShell, und suchen Sie in der Notizen-Datei nach Vorkommen von Zeilen mit dem Ausdruck ".net". Beachten Sie, dass die Anführungszeichen um den Namen des Pfads nur erforderlich sind, wenn der Pfad aus mehr als einem Wort besteht.

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

2. Durchsuchen Sie die Notizen-Datei nach Vorkommen von Zeilen mit dem Wort "Over", gefolgt von einem anderen Text. Der `SimpleMatch`-Parameter verwendet den Standardwert `false`. Bei der Suche wird die Groß-/Kleinschreibung nicht beachtet, da der `CaseSensitive`-Parameter `false`ist.

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

3. Durchsuchen Sie die Notizen-Datei mithilfe eines regulären Ausdrucks als Muster. Das Cmdlet sucht alphabetische Zeichen und Leerzeichen, die in Klammern eingeschlossen sind.

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

4. Unterscheidung nach Groß-/Kleinschreibung Durchsuchen der Notizen-Datei für Vorkommen des Worts "Parameter".

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

5. Durchsuchen Sie den mit Windows PowerShell gelieferten Variablen Anbieter nach Variablen mit numerischen Werten von 0 bis 9.

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

6. Verwenden Sie einen Skriptblock, um die Datei SelectStrCommandSample.cs nach der Zeichenfolge "POS" zu durchsuchen. Die **cmatch** -Funktion für das Skript führt eine Muster Übereinstimmung ohne Berücksichtigung der Groß-und Kleinschreibung

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

[Erstellen eines Windows PowerShell-Cmdlets](/powershell/scripting/developer/cmdlet/writing-a-windows-powershell-cmdlet)

[Erstellen Ihres ersten Cmdlets](./creating-a-cmdlet-without-parameters.md)

[Erstellen eines Cmdlets, das das System ändert](./creating-a-cmdlet-that-modifies-the-system.md)

[Entwerfen Ihres Windows PowerShell-Anbieters](../prog-guide/designing-your-windows-powershell-provider.md)

[Funktionsweise von Windows PowerShell](/previous-versions//ms714658(v=vs.85))

[Registrieren von Cmdlets, Anbietern und Host Anwendungen](/previous-versions//ms714644(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

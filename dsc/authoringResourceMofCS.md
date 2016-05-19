# Erstellen einer DSC-Ressource in C`#`

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

In der Regel wird eine benutzerdefinierte Windows PowerShell DSC-Ressource in einem PowerShell-Skript implementiert. Allerdings können Sie die Funktionalität einer benutzerdefinierten DSC-Ressource auch durch Schreiben von C#-Cmdlets implementieren. Eine Einführung zum Schreiben von Cmdlets in C# finden Sie unter [Writing a Windows PowerShell Cmdlet](https://technet.microsoft.com/en-us/library/dd878294.aspx) (Schreiben eines Windows PowerShell-Cmdlets)..

Abgesehen von der Implementierung der Ressource als Cmdlets in C# entsprechen die Schritte zum Erstellen des MOF-Schemas, zum Erstellen der Ordnerstruktur sowie zum Importieren und Verwenden Ihrer benutzerdefinierten DSC-Ressource dem unter [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md) beschriebenen Verfahren..

## Schreiben einer Cmdlet-basierten Ressource
In diesem Beispiel wird eine einfache Ressource implementiert, die eine Textdatei und deren Inhalt verwaltet.

### Schreiben des MOF-Schemas

Im folgenden sehen Sie die Definition der MOF-Ressource.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### Einrichten des Visual Studio-Projekts
#### Einrichten eines Cmdlet-Projekts

1. Öffnen Sie Visual Studio.
1. Erstellen Sie ein C#-Projekt, und geben Sie diesem einen Namen.
1. Wählen Sie **-Klassenbibliothek** aus den verfügbaren Projektvorlagen aus.
1. Klicken Sie auf **OK**..
1. Fügen Sie „System.Automation.Management.dll“ einen Assemblyverweis auf Ihr Projekt hinzu.
1. Ändern Sie den Assemblynamen so, dass er dem Namen der Ressource entspricht. In diesem Fall sollten Sie die Assembly **MSFT_XDemoFile** nennen..

### Schreiben des Codes des Cmdlets

Der folgende C#-Code implementiert die Cmdlets **Get-TargetResource**, **Set-TargetResource** und **Test-TargetResource**.

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
           } 
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
        [Parameter(Mandatory = true)]
        public string Path { get; set; }
 
        [Parameter(Mandatory = false)]
        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }
 
        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### Bereitstellen der Ressource

Die kompilierte DLL-Datei sollte in einer Dateistruktur gespeichert werden, die einer skriptbasierten Ressource ähnelt. Im folgenden finden die Ordnerstruktur für diese Ressource.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)     
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### Weitere Informationen
#### Konzepte
[Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md)
#### Weitere Ressourcen
[Schreiben eines Windows PowerShell-Cmdlets](https://msdn.microsoft.com/en-us/library/dd878294.aspx)


<!--HONumber=May16_HO2-->



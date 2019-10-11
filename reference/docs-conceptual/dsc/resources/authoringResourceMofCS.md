---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Erstellen einer DSC-Ressource in C#
ms.openlocfilehash: 6f2bb4d411237f13e2735c2e5f630b4f40dc6842
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954317"
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="b84e9-103">Erstellen einer DSC-Ressource in C\#</span><span class="sxs-lookup"><span data-stu-id="b84e9-103">Authoring a DSC resource in C\#</span></span>

> <span data-ttu-id="b84e9-104">Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b84e9-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b84e9-105">In der Regel wird eine benutzerdefinierte Windows PowerShell DSC-Ressource in einem PowerShell-Skript implementiert.</span><span class="sxs-lookup"><span data-stu-id="b84e9-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="b84e9-106">Allerdings können Sie die Funktionalität einer benutzerdefinierten DSC-Ressource auch durch Schreiben von C#-Cmdlets implementieren.</span><span class="sxs-lookup"><span data-stu-id="b84e9-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="b84e9-107">Eine Einführung zum Schreiben von Cmdlets in C# finden Sie unter [Schreiben eines Windows PowerShell-Cmdlets](/powershell/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="b84e9-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](/powershell/developer/windows-powershell).</span></span>

<span data-ttu-id="b84e9-108">Abgesehen von der Implementierung der Ressource als Cmdlets in C# entsprechen die Schritte zum Erstellen des MOF-Schemas, zum Erstellen der Ordnerstruktur sowie zum Importieren und Verwenden Ihrer benutzerdefinierten DSC-Ressource dem unter [Schreiben einer benutzerdefinierten DSC-Ressource mit MOF](authoringResourceMOF.md) beschriebenen Verfahren.</span><span class="sxs-lookup"><span data-stu-id="b84e9-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="b84e9-109">Schreiben einer Cmdlet-basierten Ressource</span><span class="sxs-lookup"><span data-stu-id="b84e9-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="b84e9-110">In diesem Beispiel wird eine einfache Ressource implementiert, die eine Textdatei und deren Inhalt verwaltet.</span><span class="sxs-lookup"><span data-stu-id="b84e9-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="b84e9-111">Schreiben des MOF-Schemas</span><span class="sxs-lookup"><span data-stu-id="b84e9-111">Writing the MOF schema</span></span>

<span data-ttu-id="b84e9-112">Im folgenden sehen Sie die Definition der MOF-Ressource.</span><span class="sxs-lookup"><span data-stu-id="b84e9-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="b84e9-113">Einrichten des Visual Studio-Projekts</span><span class="sxs-lookup"><span data-stu-id="b84e9-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="b84e9-114">Einrichten eines Cmdlet-Projekts</span><span class="sxs-lookup"><span data-stu-id="b84e9-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="b84e9-115">Öffnen Sie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b84e9-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="b84e9-116">Erstellen Sie ein C#-Projekt, und geben Sie diesem einen Namen.</span><span class="sxs-lookup"><span data-stu-id="b84e9-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="b84e9-117">Wählen Sie **-Klassenbibliothek** aus den verfügbaren Projektvorlagen aus.</span><span class="sxs-lookup"><span data-stu-id="b84e9-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="b84e9-118">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="b84e9-118">Click **Ok**.</span></span>
1. <span data-ttu-id="b84e9-119">Fügen Sie „System.Automation.Management.dll“ einen Assemblyverweis auf Ihr Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="b84e9-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="b84e9-120">Ändern Sie den Assemblynamen so, dass er dem Namen der Ressource entspricht.</span><span class="sxs-lookup"><span data-stu-id="b84e9-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="b84e9-121">In diesem Fall sollte die Assembly **MSFT_XDemoFile** benannt werden.</span><span class="sxs-lookup"><span data-stu-id="b84e9-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="b84e9-122">Schreiben des Codes des Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b84e9-122">Writing the cmdlet code</span></span>

<span data-ttu-id="b84e9-123">Der folgende C#-Code implementiert die Cmdlets **Get-TargetResource**, **Set-TargetResource** und **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="b84e9-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
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
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a><span data-ttu-id="b84e9-124">Bereitstellen der Ressource</span><span class="sxs-lookup"><span data-stu-id="b84e9-124">Deploying the resource</span></span>

<span data-ttu-id="b84e9-125">Die kompilierte DLL-Datei sollte in einer Dateistruktur gespeichert werden, die einer skriptbasierten Ressource ähnelt.</span><span class="sxs-lookup"><span data-stu-id="b84e9-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="b84e9-126">Im folgenden finden die Ordnerstruktur für diese Ressource.</span><span class="sxs-lookup"><span data-stu-id="b84e9-126">The following is the folder structure for this resource.</span></span>

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

### <a name="see-also"></a><span data-ttu-id="b84e9-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b84e9-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="b84e9-128">Konzepte</span><span class="sxs-lookup"><span data-stu-id="b84e9-128">Concepts</span></span>
[<span data-ttu-id="b84e9-129">Schreiben einer benutzerdefinierten DSC-Ressource mit MOF</span><span class="sxs-lookup"><span data-stu-id="b84e9-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="b84e9-130">Weitere Ressourcen</span><span class="sxs-lookup"><span data-stu-id="b84e9-130">Other Resources</span></span>
[<span data-ttu-id="b84e9-131">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b84e9-131">Writing a Windows PowerShell Cmdlet</span></span>](/powershell/developer/windows-powershell)
# Automatische RunAs-Unterstützung für DSC-Ressourcen
Unterstützung für RunAs-Anmeldeinformationen für DSC
--------------------------------

Die WMF 5.0 Preview-Version vom April 2015 unterstützt das Ausführen **beliebiger** DSC-Ressourcen unter einer angegebenen Gruppe von Anmeldeinformationen mithilfe der „PsDscRunAsCredential“-Eigenschaft. Dies ermöglicht Szenarien wie die Installation von MSI-Paketen in einem bestimmten Benutzerkontext, den Zugriff auf die Registrierungsstruktur eines Benutzers, auf ein bestimmtes lokales Verzeichnis eines Benutzers, auf eine Netzwerkfreigabe usw.

Das folgende Beispiel zeigt, wie die „PsDscRunAsCredential“-Eigenschaft in DSC verwendet wird, um die Hintergrundfarbe der Eingabeaufforderung eines Benutzers zu ändern.

Configuration ChangeCmdBackGroundColor

{

    Node ("localhost")

    {

        Registry CmdPath

        {

            Key = "HKEY\_CURRENT\_USER\\\\Software\\Microsoft\\\\Command Processor"

            ValueName = "DefaultColor"

            ValueData = '1F'

            ValueType = "DWORD"

            Ensure = "Present"

            Force = $true

            Hex = $true

            PsDscRunAsCredential = get-credential

        }

    }

}

$configData = @{

AllNodes = @(

@{

NodeName="localhost";

CertificateFile = "C:\\publicKeys\\targetNode.cer"

}

)

}

ChangeCmdBackGroundColor -ConfigurationData $configData

## Bekannte Probleme

In dieser Version gibt es die folgenden bekannten Probleme mit dem DSC-Feature der RunAs-Anmeldeinformationen:

-   Die Ressource „WindowsProcess“ unterstützt keine RunAs-Anmeldeinformationen.

<!--HONumber=Mar16_HO2-->

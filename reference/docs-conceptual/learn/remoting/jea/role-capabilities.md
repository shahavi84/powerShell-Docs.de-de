---
ms.date: 07/10/2019
keywords: jea,powershell,security
title: JEA-Rollenfunktionen
ms.openlocfilehash: 5b5b5977d4fec1ed850f1146fe7c09463908651b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402397"
---
# <a name="jea-role-capabilities"></a>JEA-Rollenfunktionen

Beim Erstellen eines JEA-Endpunkts müssen Sie eine oder mehrere Rollenfunktionen definieren, die festlegen, welche Befehle ein Benutzer in einer JEA-Sitzung ausführen kann. Eine Rollenfunktion ist eine PowerShell-Datendatei mit der Erweiterung `.psrc`. Sie enthält alle Cmdlets, Funktionen, Anbieter und externen Programme für Benutzer, die eine Verbindung herstellen.

## <a name="determine-which-commands-to-allow"></a>Festlegen der zulässigen Befehle

Die erste Frage beim Erstellen einer Rollenfunktionsdatei lautet: Worauf müssen die Benutzer zugreifen können? Das Erfassen dieser Informationen kann relativ zeitaufwendig sein, ist aber ein sehr wichtiger Prozess. Benutzer, deren Zugriff auf zu wenige Cmdlets und Funktionen beschränkt ist, können ihre jeweiligen Aufgaben möglicherweise nicht ausführen. Wenn Benutzer Zugriff auf zu viele Cmdlets und Funktionen haben, haben sie mehr Berechtigungen, als Sie vorgesehen haben, was ein Sicherheitsproblem darstellen kann.

Die Art und Weise, wie Sie diesen Prozess durchführen, richtet sich nach Ihrer Organisation und Ihren Zielen. Die folgenden Tipps können Ihnen dabei helfen.

1. **Identifizieren** Sie die Befehle, die Benutzer verwenden, um ihre Arbeit zu erledigen. Dazu müssen Sie möglicherweise IT-Mitarbeiter befragen, Automatisierungsskripts überprüfen oder PowerShell-Sitzungsaufzeichnungen und -protokolle analysieren.
2. **Aktualisieren** Sie, soweit möglich, die Verwendung von Befehlszeilentools auf PowerShell-Entsprechungen, und sorgen Sie dadurch für eine optimale Überwachung und JEA-Anpassungserfahrung. Externe Programme können in JEA nicht so präzise wie native PowerShell-Cmdlets und -Funktionen beschränkt werden.
3. **Beschränken** Sie den Gültigkeitsbereich der Cmdlets, falls erforderlich, um nur bestimmte Parameter oder Parameterwerte zuzulassen. Dies ist besonders wichtig, wenn die Benutzer nur einen Teil eines Systems verwalten sollen.
4. **Erstellen** Sie benutzerdefinierte Funktionen, um komplexe Befehle zu ersetzen bzw. Befehle, die in JEA nur schwer einzuschränken sind. Eine einfache Funktion, die einen komplexen Befehl enthält oder zusätzliche Validierungslogik anwendet, bietet Administratoren zusätzliche Kontrolle und sorgt für mehr Benutzerfreundlichkeit bei Endbenutzern.
5. **Testen** Sie die entsprechende Liste von zulässigen Befehlen mit Ihren Benutzern oder Automatisierungsservices, und nehmen Sie bei Bedarf Anpassungen vor.

### <a name="examples-of-potentially-dangerous-commands"></a>Beispiele für potenziell gefährliche Befehle

Die Befehle sollten sorgfältig ausgewählt werden, um sicherzustellen, dass der JEA-Endpunkt dem Benutzer keine Möglichkeit gibt, seine Berechtigungen zu erhöhen.

> [!IMPORTANT]
> Wichtige Informationen für Benutzer. Befehle in einer JEA-Sitzung werden häufig mit erhöhten Rechten ausgeführt.

In der folgenden Tabelle finden Sie Beispiele für Befehle, die böswillig verwendet werden können, wenn sie uneingeschränkt zur Verfügung stehen. Dies ist keine vollständige Liste und lediglich als einleitende Vorsichtsmaßnahme gedacht.

|                                            Risiko                                            |                                Beispiel                                |                                                                              Verwandte Befehle                                                                              |
| ------------------------------------------------------------------------------------------ | --------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gewähren von Administratorberechtigungen für Benutzer, die eine Verbindung aufbauen, um JEA zu umgehen                                | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`                                                                                                        |
| Ausführen von beliebigem Code, z.B. Malware, Exploits oder benutzerdefinierten Skripts, um Schutzmechanismen zu umgehen | `Start-Process -FilePath '\\san\share\malware.exe'`                   | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob` |

## <a name="create-a-role-capability-file"></a>Erstellen einer Rollenfunktionsdatei

Sie können eine neue PowerShell-Rollenfunktionsdatei mit dem [New-PSRoleCapabilityFile](/powershell/module/microsoft.powershell.core/new-psrolecapabilityfile?view=powershell-6)-Cmdlet erstellen.

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Die resultierende Rollenfunktionsdatei sollte bearbeitet werden, um die für die Rolle erforderlichen Befehle zuzulassen. Die PowerShell-Hilfedokumentation enthält mehrere Beispiele dafür, wie Sie die Datei konfigurieren können.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Zulassen von PowerShell-Cmdlets und -Funktionen

Fügen Sie den Feldern „VisibleCmdlets“ oder „VisibleFunctions“ den Cmdlet- oder Funktionsnamen hinzu, um Benutzern das Ausführen von PowerShell-Cmdlets oder -Funktionen zu ermöglichen. Wenn Sie nicht sicher sind, ob es sich um einen Befehl für ein Cmdlet oder eine Funktion handelt, können Sie `Get-Command <name>` ausführen und die **CommandType**-Eigenschaft in der Ausgabe überprüfen.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

Manchmal ist der Gültigkeitsbereich eines bestimmten Cmdlets oder einer Funktion für die Anforderungen Ihrer Benutzer zu weit gefasst. Ein DNS-Administrator z.B. muss wahrscheinlich nur über Zugriff verfügen, um den DNS-Dienst neu zu starten. In Umgebungen mit mehreren Mandanten haben Mandanten Zugriff auf Self-Service-Verwaltungstools. Die Mandanten sollten auf die Verwaltung ihrer eigenen Ressourcen beschränkt werden. In einem solchen Fall können Sie festlegen, welche Parameter vom Cmdlet oder der Funktion verfügbar gemacht werden.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}
```

In komplexeren Szenarios müssen Sie möglicherweise auch beschränken, welche Werte ein Benutzer mit diesen Parametern verwenden darf. Anhand von Rollenfunktionen können Sie einen Satz von Werten oder das Muster eines regulären Ausdrucks definieren, um zulässige Eingaben festzulegen.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> Die [allgemeinen PowerShell-Parameter](/powershell/module/microsoft.powershell.core/about/about_commonparameters) sind immer zulässig, selbst wenn Sie die verfügbaren Parameter beschränken.
> Sie brauchen sie nicht explizit im Parameter-Feld aufzuführen.

Die folgende Tabelle beschreibt die verschiedenen Methoden, mit denen Sie ein sichtbares Cmdlet bzw. eine sichtbare Funktion anpassen können.
Sie können alle unten aufgeführten Cmdlets und Funktionen im Feld **VisibleCmdlets** frei miteinander kombinieren.

|                                           Beispiel                                           |                                                             Anwendungsfall                                                              |
| ------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| `'My-Func'` oder `@{ Name = 'My-Func' }`                                                      | Ermöglicht dem Benutzer das Ausführen von `My-Func` ohne jegliche Einschränkungen bei den Parametern                                                      |
| `'MyModule\My-Func'`                                                                        | Ermöglicht dem Benutzer das Ausführen von `My-Func` vom Modul `MyModule` ohne jegliche Einschränkungen bei den Parametern                           |
| `'My-*'`                                                                                    | Ermöglicht dem Benutzer das Ausführen eines beliebigen Cmdlets oder einer beliebigen Funktion mit dem Verb `My`                                                                 |
| `'*-Func'`                                                                                  | Ermöglicht dem Benutzer das Ausführen eines beliebigen Cmdlets oder einer beliebigen Funktion mit dem Namen `Func`                                                               |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`              | Ermöglicht dem Benutzer das Ausführen von `My-Func` mit den Parametern `Param1` und `Param2`. Für die Parameter kann ein beliebiger Wert angegeben werden.          |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}` | Ermöglicht dem Benutzer das Ausführen von `My-Func` mit dem Parameter `Param1`. Für den Parameter kann nur „Value1“ und „Value2“ angegeben werden.        |
| `@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`    | Ermöglicht dem Benutzer das Ausführen von `My-Func` mit dem Parameter `Param1`. Für den Parameter kann ein beliebiger Wert, beginnend mit „Contoso“, angegeben werden. |

> [!WARNING]
> Bewährten Sicherheitsmaßnahmen zufolge wird bei der Definition sichtbarer Cmdlets und Funktionen empfohlen, keine Platzhalter zu verwenden. Stattdessen sollten Sie jeden vertrauenswürdigen Befehl einzeln aufführen, um sicherzustellen, dass Befehle, die dem gleichen Namensschema folgen, nicht unbeabsichtigt autorisiert werden.

Sie können nicht gleichzeitig ein **ValidatePattern**- und ein **ValidateSet**-Attribut auf das gleiche Cmdlet oder die gleiche Funktion anwenden.

Andernfalls wird das **ValidateSet**-Attribut vom **ValidatePattern**-Attribut überschrieben.

Weitere Informationen zum **ValidatePattern**-Attribut finden Sie [im englischsprachigen Blogbeitrag *Hey, Scripting Guy!* ](https://devblogs.microsoft.com/scripting/validate-powershell-parameters-before-running-the-script/) und im Referenzmaterial [PowerShell Regular Expressions](/powershell/module/microsoft.powershell.core/about/about_regular_expressions) (Reguläre Ausdrücke in PowerShell).

### <a name="allowing-external-commands-and-powershell-scripts"></a>Zulassen von externen Befehlen und PowerShell-Skripts

Um Benutzern das Ausführen von ausführbaren Dateien und PowerShell-Skripts (.ps1) in einer JEA-Sitzung zu ermöglichen, müssen Sie den vollständigen Pfad zu jedem einzelnen Programm im Feld **VisibleExternalCommands** hinzufügen.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

Außerdem sollten Sie möglichst mit den PowerShell-Cmdlet- bzw. -Funktionsentsprechungen der von Ihnen autorisierten ausführbaren Dateien arbeiten, da Sie so bestimmen können, welche Parameter für PowerShell-Cmdlets bzw. -Funktionen zulässig sind.

Bei vielen ausführbaren Dateien können Sie den aktuellen Status lesen und ändern, indem Sie andere Parameter angeben.

Betrachten Sie beispielsweise die Rolle eines Serveradministrators, der in einem System gehostete Netzwerkfreigaben verwaltet. Eine Möglichkeit zum Verwalten von Dateifreigaben ist `net share`. Die Verwendung von **net.exe** ist allerdings mit Gefahren verbunden, denn der Benutzer könnte den Befehl auch nutzen, um sich mithilfe von `net group Administrators unprivilegedjeauser /add` Administratorberechtigungen zu verschaffen. Eine sicherere Möglichkeit ist die Verwendung von [Get-SmbShare](/powershell/module/smbshare/get-smbshare). Dieses Cmdlet sorgt für das gleiche Ergebnis, verfügt jedoch über einen weitaus eingeschränkteren Geltungsbereich.

Wenn Sie externe Befehle für Benutzer in einer JEA-Sitzung verfügbar machen, geben Sie immer den vollständigen Pfad zur ausführbaren Datei an. So wird die Ausführung ähnlich benannter und potenziell schädlicher Programme verhindert, die an anderer Stelle im System gespeichert sind.

### <a name="allowing-access-to-powershell-providers"></a>Zulassen von Zugriffssteuerung für PowerShell-Anbieter

Standardmäßig sind in JEA-Sitzungen keine PowerShell-Anbieter verfügbar. Hierdurch wird verhindert, dass vertrauliche Informationen und Konfigurationseinstellungen an Benutzer weitergegeben werden, die eine Verbindung herstellen.

Bei Bedarf können Sie den Zugriff auf die PowerShell-Anbieter über den Befehl `VisibleProviders` ermöglichen. Sie erhalten eine vollständige Liste aller Anbieter, indem Sie `Get-PSProvider` ausführen.

```powershell
VisibleProviders = 'Registry'
```

Für einfache Aufgaben, die Zugriff auf das Dateisystem, die Registrierung, den Zertifikatspeicher oder andere vertrauliche Anbieter voraussetzen, können Sie auch eine benutzerdefinierte Funktion in Erwägung ziehen, die einen Zugriff auf den Anbieter im Auftrag des Benutzers ermöglicht. Die Funktionen, Cmdlets und externen Programme, die in einer JEA-Sitzung verfügbar sind, unterliegen nicht den gleichen Einschränkungen wie JEA. Sie können standardmäßig auf alle Anbieter zugreifen. Sie können auch das [Benutzerlaufwerk](session-configurations.md#user-drive) verwenden, wenn Sie Dateien auf einen bzw. von einem JEA-Endpunkt kopieren müssen.

### <a name="creating-custom-functions"></a>Erstellen von benutzerdefinierten Funktionen

Sie können benutzerdefinierte Funktionen in einer Rollenfunktionsdatei erstellen, um komplexe Aufgaben für Ihre Endbenutzer zu vereinfachen. Benutzerdefinierte Funktionen erweisen sich als nützlich, wenn für Cmdlet-Parameterwerte eine erweiterte Validierungslogik erforderlich ist. Sie können einfache Funktionen in das Feld **FunctionDefinitions** schreiben:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending |
            Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Vergessen Sie nicht, den Namen der benutzerdefinierten Funktionen im Feld **VisibleFunctions** hinzuzufügen, damit sie von den JEA-Benutzern ausgeführt werden können.

Textkörper (Skriptblöcke) von benutzerdefinierten Funktionen werden im Standardsprachmodus für das System ausgeführt und unterliegen nicht den JEA-Spracheinschränkungen. Dies bedeutet, dass Funktionen Zugriff auf das Dateisystem und die Registrierung haben und Befehle ausführen können, die in der Rollenfunktionsdatei nicht sichtbar gemacht wurden. Vermeiden Sie das Ausführen von beliebigem Code bei der Verwendung von Parametern. Vermeiden Sie das Piping von Benutzereingaben direkt an Cmdlets wie `Invoke-Expression`.

Im Beispiel oben sehen Sie, dass der vollqualifizierte Modulname (FQMN) `Microsoft.PowerShell.Utility\Select-Object` anstelle der Kurzschreibweise `Select-Object` verwendet wurde.
Funktionen, die in Rollenfunktionsdateien definiert werden, unterliegen weiterhin dem Gültigkeitsbereich von JEA-Sitzungen. Darunter fallen auch die Proxyfunktionen, die JEA erstellt, um vorhandene Befehle einzuschränken.

`Select-Object` ist standardmäßig in allen JEA-Sitzungen ein eingeschränktes Cmdlet, das eine Auswahl beliebiger Eigenschaften für Objekte nicht zulässt. Um `Select-Object` uneingeschränkt in Funktionen verwenden zu können, müssen Sie die vollständige Implementierung explizit durch Angabe der FQMN anfordern. Alle eingeschränkten Cmdlets in einer JEA-Sitzung haben die gleichen Einschränkungen, wenn sie aus einer Funktion aufgerufen werden. Weitere Informationen finden Sie unter [about_Command_Precedence](/powershell/module/microsoft.powershell.core/about/about_command_precedence).

Wenn Sie mehrere benutzerdefinierte Funktionen schreiben, ist es einfacher, diese in einem PowerShell-Skriptmodul zu speichern. Sie können diese Funktionen anschließend in der JEA-Sitzung mithilfe des **VisibleFunctions**-Felds genauso sichtbar machen wie integrierte und Drittanbietermodule.

Damit die Registerkartenvervollständigung in JEA-Sitzungen ordnungsgemäß funktioniert, müssen Sie die integrierte Funktion `tabexpansion2` in die Liste **VisibleFunctions** einbeziehen.

## <a name="make-the-role-capabilities-available-to-a-configuration"></a>Verfügbarmachen der Rollenfunktionen für eine Konfiguration

Damit PowerShell in Versionen vor PowerShell 6 eine Rollenfunktionsdatei erkennen kann, müssen Sie diese im Ordner **RoleCapabilities** in einem PowerShell-Modul speichern. Das Modul kann in einem beliebigen Ordner gespeichert werden, der in der Umgebungsvariablen `$env:PSModulePath` enthalten ist. Sie sollten das Modul jedoch nicht in `$env:SystemRoot\System32` oder in einen Ordner einfügen, dessen Dateien von nicht vertrauenswürdigen Benutzern geändert werden können.

Im folgenden Beispiel wird ein PowerShell-Skriptmodul namens **ContosoJEA** zum Hosten der Rollenfunktionsdatei im `$env:ProgramFiles`-Pfad erstellt.

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest.
# At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Weitere Informationen zu PowerShell-Modulen finden Sie in den [Grundlagen zu PowerShell-Modulen](/powershell/scripting/developer/windows-powershell).

Ab PowerShell 6 wird die Eigenschaft **RoleDefinitions** der Sitzungskonfigurationsdatei hinzugefügt. Mit dieser Eigenschaft können Sie den Speicherort einer Rollenkonfigurationsdatei für die Rollendefinition angeben. Siehe Beispiele in [New-PSSessionConfigurationFile](/powershell/module/microsoft.powershell.core/new-pssessionconfigurationfile).

## <a name="updating-role-capabilities"></a>Aktualisieren von Rollenfunktionen

Sie können eine Rollenfunktionsdatei jederzeit bearbeiten, um die Einstellungen zu aktualisieren. Jede neue JEA-Sitzung, die nach dem Aktualisieren der Rollenfunktion gestartet wird, enthält die überarbeiteten Funktionen.

Aus diesem Grund ist es so wichtig, den Zugriff auf den Rollenfunktionsordner genau zu steuern. Nur sehr vertrauenswürdige Administratoren sollten Rollenfunktionsdateien ändern können. Wenn nicht vertrauenswürdige Benutzer berechtigt sind, Rollenfunktionsdateien zu ändern, können sie sich leicht selbst Zugriff auf Cmdlets verschaffen und damit ihre eigenen Berechtigungen erhöhen.

Administratoren, die den Zugriff auf die Rollenfunktionen einschränken möchten, müssen sicherstellen, dass das lokale System über Lesezugriff auf die Rollenfunktionsdateien und die darin enthaltenen Module verfügt.

## <a name="how-role-capabilities-are-merged"></a>Zusammenführung von Rollenfunktionen

Die Benutzer erhalten Zugriff auf alle übereinstimmenden Rollenfunktionen in der [Sitzungskonfigurationsdatei](session-configurations.md), wenn sie eine JEA-Sitzung beginnen. JEA versucht, den Benutzern den Satz von Befehlen mit den höchsten Berechtigungen zur Verfügung zu stellen, die für die Rollen zulässig sind.

### <a name="visiblecmdlets-and-visiblefunctions"></a>VisibleCmdlets und VisibleFunctions

Die komplexe Zusammenführungslogik wirkt sich auf Cmdlets und Funktionen aus, deren Parameter und Parameterwerte in JEA eingeschränkt sein können.

Die folgenden Regeln gelten:

1. Wenn ein Cmdlet nur in einer Rolle sichtbar gemacht wird, ist es für Benutzer mit beliebigen Parametereinschränkungen sichtbar.
2. Wenn ein Cmdlet in mehr als einer Rolle sichtbar gemacht wird und jede Rolle über dieselben Einschränkungen für das Cmdlet verfügt, ist das Cmdlet für Benutzer mit diesen Einschränkungen sichtbar.
3. Wenn ein Cmdlet in mehr als einer Rolle sichtbar gemacht wird und jede Rolle einen anderen Satz von Parametern zulässt, sind das Cmdlet und alle für jede Rolle definierten Parameter für die Benutzer sichtbar.
   Wenn für eine Rolle keine Einschränkungen für die Parameter gelten, sind alle Parameter zulässig.
4. Wenn eine Rolle ein ValidateSet- oder ein ValidatePattern-Attribut für einen Cmdlet-Parameter definiert und die andere Rolle den Parameter zwar zulässt, aber die Parameterwerte nicht einschränkt, werden das ValidateSet- bzw. das ValidatePattern-Attribut ignoriert.
5. Wenn für den gleichen Cmdlet-Parameter in mehr als einer Rolle ein ValidateSet-Attribut definiert ist, sind alle Werte aller ValidateSet-Attribute zulässig.
6. Wenn für den gleichen Cmdlet-Parameter in mehr als einer Rolle ein ValidatePattern-Attribut definiert ist, sind alle Werte, die einem beliebigen ValidatePattern-Attribut entsprechen, zulässig.
7. Wenn ein ValidateSet-Attribut in einer oder mehreren Rollen definiert ist und ein ValidatePattern-Attribut in einer anderen Rolle für den gleichen Cmdlet-Parameter definiert ist,wird das ValidateSet-Attribut ignoriert und für die übrigen ValidatePattern-Attribute gilt Regel 6.

Das nachstehende Beispiel zeigt, wie Rollen gemäß geltenden Regeln zusammengeführt werden:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service
#   is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use
#   ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service';
                        Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

### <a name="visibleexternalcommands-visiblealiases-visibleproviders-scriptstoprocess"></a>VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess

Alle anderen Felder in der Rollenfunktionsdatei werden einem kumulativen Satz von zulässigen externen Befehlen, Aliasen, Anbietern und Startskripts hinzugefügt. Alle in einer Rollenfunktion verfügbaren Befehle, Aliase, Anbieter oder Skripts sind für JEA-Benutzer verfügbar.

Achten Sie darauf, dass die kombinierte Gruppe der Anbieter einer Rollenfunktion und der Anbieter von Cmdlets/Funktionen/Befehlen einer anderen Rollenfunktion den Benutzern keinen unbeabsichtigten Zugriff auf Systemressourcen gibt.
Wenn eine Rolle z.B. das `Remove-Item`-Cmdlet zulässt und eine andere den `FileSystem`-Anbieter, besteht die Gefahr, dass ein JEA-Benutzer beliebige Dateien auf Ihrem Computer löscht. Weitere Informationen dazu, wie die geltenden Berechtigungen von Benutzern ermittelt werden können, finden Sie im Artikel [Auditing and Reporting on JEA (Überprüfen und Erstellen von Berichten mit JEA)](audit-and-report.md).

## <a name="next-steps"></a>Nächste Schritte

[Create a session configuration file (Erstellen einer Sitzungskonfigurationsdatei)](session-configurations.md)

---
ms.date: 09/09/2019
keywords: powershell,cmdlet
title: Anhang 1 – Kompatibilitätsaliase
ms.openlocfilehash: 2351fdf23711fe1417f7e3fc3cca5b642d5a59fc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "70848159"
---
# <a name="appendix-1---compatibility-aliases"></a>Anhang 1: Kompatibilitätsaliase

PowerShell verfügt über mehrere Aliase, die **UNIX**- und **cmd.exe**-Benutzern ermöglichen, vertraute Befehle zu verwenden.
Die Befehle, das zugehörige PowerShell-Cmdlet und der PowerShell-Alias sind in der folgenden Tabelle aufgeführt:

|Befehl „cmd. exe“|UNIX-Befehl|PowerShell-Cmdlet|PowerShell-Alias|
|---------------|----------------|--------------|------------|
|**cls**|**Löschen**|`Clear-Host` (Funktion)|`cls`|
|**copy**|**cp**|`Copy-Item`|`cpi`|
|**dir**|**ls**|`Get-ChildItem`|`gci`|
|**type**|**cat**|`Get-Content`|`gc`|
|**move**|**mv**|`Move-Item`|`mi`|
|**md**|**mkdir**|`New-Item`|`ni`|
|**pushd**|**pushd**|`Push-Location`|`pushd`|
|**popd**|**popd**|`Pop-Location`|`popd`|
|**del**, **erase**, **rd**, **rmdir**|**rm**|`Remove-Item`|`ri`|
|**ren**|**mv**|`Rename-Item`|`rni`|
|**cd**, **chdir**|**cd**|`Set-Location`|`sl`|

Verwenden Sie das [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias)-Cmdlet, um die PowerShell-Aliase zu ermitteln. Um die Aliase eines Cmdlets anzuzeigen, verwenden Sie den **Definition**-Parameter, und geben Sie den Namen des Cmdlets an.
Verwenden Sie alternativ den **Name**-Parameter, um den Cmdlet-Namen eines Alias zu suchen.

```powershell
Get-Alias -Definition Get-ChildItem
```

```Output
CommandType     Name
-----------     ----
Alias           dir -> Get-ChildItem
Alias           gci -> Get-ChildItem
Alias           ls -> Get-ChildItem
```

```powershell
Get-Alias -Name gci
```

```Output
CommandType     Name
-----------     ----
Alias           gci -> Get-ChildItem
```

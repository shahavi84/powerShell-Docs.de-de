---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: "Abrufen von Informationen über Befehle"
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="adcbe-103">Abrufen von Informationen über Befehle</span><span class="sxs-lookup"><span data-stu-id="adcbe-103">Getting Information About Commands</span></span>
<span data-ttu-id="adcbe-104">Das Windows PowerShell-Cmdlet **Get-Command** ruft alle Befehle ab, die in Ihrer aktuellen Sitzung verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="adcbe-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="adcbe-105">Wenn Sie **Get-Command** an einer Windows PowerShell-Eingabeaufforderung eingeben, erhalten Sie eine Ausgabe wie die folgende:</span><span class="sxs-lookup"><span data-stu-id="adcbe-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="adcbe-106">Diese Ausgabe sieht der Hilfe-Ausgabe von „Cmd.exe“ sehr ähnlich: eine tabellarische Zusammenfassung der internen Befehle.</span><span class="sxs-lookup"><span data-stu-id="adcbe-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="adcbe-107">Im Auszug der oben gezeigten **Get-Command**-Befehlsausgabe hat jeder aufgeführte Befehl den Befehlstyp (CommandType) „Cmdlet“.</span><span class="sxs-lookup"><span data-stu-id="adcbe-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="adcbe-108">Ein Cmdlet ist der systeminterne Befehlstyp in Windows PowerShell, d.h. ein Typ, der ungefähr den Befehlen **dir** und **cd** von „Cmd.exe“ sowie integrierten Befehlen von UNIX-Shells wie BASH entspricht.</span><span class="sxs-lookup"><span data-stu-id="adcbe-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="adcbe-109">In der Ausgabe des Befehls **Get-Command** enden alle Definitionen mit Auslassungspunkten (...), um anzugeben, dass PowerShell nicht alle Inhalte im verfügbaren Platz anzeigen kann.</span><span class="sxs-lookup"><span data-stu-id="adcbe-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="adcbe-110">Wenn Windows PowerShell Ausgabe anzeigt, wird diese als Text formatiert und so angeordnet, dass sie genau ins Fenster passt.</span><span class="sxs-lookup"><span data-stu-id="adcbe-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="adcbe-111">Dies wird später in dem Abschnitt erläutert, in dem es um Formatierer geht.</span><span class="sxs-lookup"><span data-stu-id="adcbe-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="adcbe-112">Das Cmdlet **Get-Command** hat einen **Syntax**-Parameter, mit dem die Syntax jedes Cmdlets abgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="adcbe-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="adcbe-113">Verwenden Sie den folgenden Befehl, um die Syntax des Cmdlets „Get-Help“ abzurufen:</span><span class="sxs-lookup"><span data-stu-id="adcbe-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="adcbe-114">**Get-Command Get-Help-Syntax**</span><span class="sxs-lookup"><span data-stu-id="adcbe-114">**Get-Command Get-Help -Syntax**</span></span>

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### <a name="displaying-available-command-types"></a><span data-ttu-id="adcbe-115">Anzeigen von verfügbaren Befehlstypen</span><span class="sxs-lookup"><span data-stu-id="adcbe-115">Displaying Available Command Types</span></span>
<span data-ttu-id="adcbe-116">Der Befehl **Get-Command** listet nicht jeden der Befehle auf, der in Windows PowerShell verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="adcbe-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="adcbe-117">Stattdessen listet der Befehl **Get-Command** nur die Cmdlets auf, die es in der aktuellen Sitzung gibt.</span><span class="sxs-lookup"><span data-stu-id="adcbe-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="adcbe-118">Windows PowerShell unterstützt tatsächlich mehrere weitere Befehlstypen.</span><span class="sxs-lookup"><span data-stu-id="adcbe-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="adcbe-119">Aliase, Funktionen und Skripts sind ebenfalls Windows PowerShell-Befehle, obwohl sie nicht ausführlich im Windows PowerShell-Benutzerhandbuch erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="adcbe-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="adcbe-120">Auch externe Dateien, die ausführbar sind oder einen registrierten Dateityphandler haben, werden als Befehle klassifiziert.</span><span class="sxs-lookup"><span data-stu-id="adcbe-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="adcbe-121">Um alle Befehle in der Sitzung aufzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="adcbe-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="adcbe-122">Da diese Liste externe Dateien in Ihrem Suchpfad einschließt, kann sie Tausende von Elementen enthalten.</span><span class="sxs-lookup"><span data-stu-id="adcbe-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="adcbe-123">Es ist sinnvoller, einen reduzierten Satz von Befehlen anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="adcbe-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="adcbe-124">Um systemeigene Befehle anderer Typen abzurufen, verwenden Sie den **CommandType**-Parameter des Cmdlets **Get-Command**.</span><span class="sxs-lookup"><span data-stu-id="adcbe-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="adcbe-125">Das Sternchen (\*) wird zum Abgleichen mit Platzhalterzeichen in Windows PowerShell-Befehlsargumenten verwendet.</span><span class="sxs-lookup"><span data-stu-id="adcbe-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="adcbe-126">\* bedeutet „Abgleichen mit einem oder mehreren beliebigen Zeichen“.</span><span class="sxs-lookup"><span data-stu-id="adcbe-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="adcbe-127">Beispielsweise können Sie **Get-Command a\&#42;** eingeben, um nach allen Befehlen zu suchen, die mit dem Buchstaben „a“ beginnen.</span><span class="sxs-lookup"><span data-stu-id="adcbe-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="adcbe-128">Anders als beim Abgleichen mit Platzhalterzeichen in „Cmd.exe“ stimmt das Windows PowerShell-Platzhalterzeichen auch mit einem Punkt überein.</span><span class="sxs-lookup"><span data-stu-id="adcbe-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="adcbe-129">Geben Sie Folgendes ein, um Befehlsaliase abzurufen, bei denen es sich um die zugewiesenen Spitznamen von Befehlen handelt:</span><span class="sxs-lookup"><span data-stu-id="adcbe-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="adcbe-130">Um die Funktionen in der aktuellen Sitzung abzurufen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="adcbe-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="adcbe-131">Um Skripts im Suchpfad von Windows PowerShell anzuzeigen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="adcbe-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```

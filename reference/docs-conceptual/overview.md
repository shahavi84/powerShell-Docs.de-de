---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: PowerShell-Skripterstellung
ms.openlocfilehash: 07925ce8dcafd33970a703c9b241bf6f76f88d10
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401685"
---
# <a name="powershell"></a><span data-ttu-id="e8b0a-103">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8b0a-103">PowerShell</span></span>

<span data-ttu-id="e8b0a-104">PowerShell ist eine aufgabenbasierte Befehlszeilenshell und Skriptsprache, die auf .NET basiert.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-104">PowerShell is a task-based command-line shell and scripting language built on .NET.</span></span>
<span data-ttu-id="e8b0a-105">Mit PowerShell können Systemadministratoren und Poweruser Aufgaben zum Verwalten von Betriebssystemen (Linux, macOS und Windows) und Prozessen schnell automatisieren.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-105">PowerShell helps system administrators and power-users rapidly automate tasks that manage operating systems (Linux, macOS, and Windows) and processes.</span></span>

<span data-ttu-id="e8b0a-106">Über PowerShell-Befehle können Sie Computer mit der Befehlszeile verwalten.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-106">PowerShell commands let you manage computers from the command line.</span></span> <span data-ttu-id="e8b0a-107">Mithilfe von PowerShell-Anbietern können Sie auf Datenspeicher wie die Registrierung und den Zertifikatspeicher genauso einfach zugreifen wie auf das Dateisystem.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-107">PowerShell providers let you access data stores, such as the registry and certificate store, as easily as you access the file system.</span></span> <span data-ttu-id="e8b0a-108">PowerShell verfügt über einen umfangreichen Ausdrucksparser und eine vollständig entwickelte Skriptsprache.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-108">PowerShell includes a rich expression parser and a fully developed scripting language.</span></span>

## <a name="powershell-is-open-source"></a><span data-ttu-id="e8b0a-109">PowerShell ist Open Source</span><span class="sxs-lookup"><span data-stu-id="e8b0a-109">PowerShell is open-source</span></span>

<span data-ttu-id="e8b0a-110">Der grundlegende PowerShell-Quellcode ist jetzt auf GitHub verfügbar und für Community-Beiträge offen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-110">PowerShell base source code is now available in GitHub and open to community contributions.</span></span>
<span data-ttu-id="e8b0a-111">Informationen dazu finden Sie unter [PowerShell-Quellcode auf GitHub](https://github.com/powershell/powershell).</span><span class="sxs-lookup"><span data-stu-id="e8b0a-111">See [PowerShell source on GitHub](https://github.com/powershell/powershell).</span></span>

<span data-ttu-id="e8b0a-112">Sie können sich alles Notwendige [hier](https://github.com/PowerShell/PowerShell#get-powershell) im Abschnitt „Get PowerShell“ (PowerShell herunterladen) herunterladen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-112">You can start with the bits you need at [Get PowerShell](https://github.com/PowerShell/PowerShell#get-powershell).</span></span>
<span data-ttu-id="e8b0a-113">Beginnen Sie alternativ mit einer kurzen Einführung unter [Getting Started (Erste Schritte)](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span><span class="sxs-lookup"><span data-stu-id="e8b0a-113">Or, perhaps, with a quick tour at [Getting Started](https://github.com/PowerShell/PowerShell/blob/master/docs/learning-powershell).</span></span>

## <a name="powershell-design-goals"></a><span data-ttu-id="e8b0a-114">PowerShell-Entwurfsziele</span><span class="sxs-lookup"><span data-stu-id="e8b0a-114">PowerShell design goals</span></span>

<span data-ttu-id="e8b0a-115">PowerShell soll Befehlszeilen- und Skriptumgebungen verbessern. Es beseitigt lange bestehende Probleme und führt neue Features ein.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-115">PowerShell is designed to improve the command-line and scripting environment by eliminating long-standing problems and adding new features.</span></span>

### <a name="discoverability"></a><span data-ttu-id="e8b0a-116">Erkennbarkeit</span><span class="sxs-lookup"><span data-stu-id="e8b0a-116">Discoverability</span></span>

<span data-ttu-id="e8b0a-117">Sie können sich leicht mit den Features in PowerShell vertraut machen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-117">PowerShell makes it easy to discover its features.</span></span> <span data-ttu-id="e8b0a-118">Um z. B. eine Liste von Cmdlets zu finden, die zum Anzeigen und Ändern von Windows-Diensten dienen, geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="e8b0a-118">For example, to find a list of cmdlets that view and change Windows services, type:</span></span>

```powershell
Get-Command *-Service
```

<span data-ttu-id="e8b0a-119">Nachdem Sie ermittelt haben, welches Cmdlet welche Aufgabe erledigt, können Sie mithilfe des Cmdlets `Get-Help` mehr über das Cmdlet erfahren.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-119">After discovering which cmdlet accomplishes a task, you can learn more about the cmdlet by using the `Get-Help` cmdlet.</span></span> <span data-ttu-id="e8b0a-120">Geben Sie z.B. zum Anzeigen der Hilfe zum Cmdlet `Get-Service` Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="e8b0a-120">For example, to display help about the `Get-Service` cmdlet, type:</span></span>

```powershell
Get-Help Get-Service
```

<span data-ttu-id="e8b0a-121">Die meisten Cmdlets geben Objekte zurück, die bearbeitet und dann als Text für die Anzeige gerendert werden können.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-121">Most cmdlets return objects that can be manipulated and then rendered as text for display.</span></span> <span data-ttu-id="e8b0a-122">Um die Ausgabe eines Cmdlets vollständig zu verstehen, leiten Sie die Ausgabe an das Cmdlet `Get-Member` weiter.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-122">To fully understand the output of a cmdlet, pipe the output to the `Get-Member` cmdlet.</span></span> <span data-ttu-id="e8b0a-123">Der folgende Befehl zeigt z.B. Informationen zu den Elementen des Objekts an, das vom Cmdlet `Get-Service` ausgegeben wurde.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-123">For example, the following command displays information about the members of the object output by the `Get-Service` cmdlet.</span></span>

```powershell
Get-Service | Get-Member
```

### <a name="consistency"></a><span data-ttu-id="e8b0a-124">Konsistenz</span><span class="sxs-lookup"><span data-stu-id="e8b0a-124">Consistency</span></span>

<span data-ttu-id="e8b0a-125">Das Verwalten von Systemen kann eine komplexe Aufgabe sein.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-125">Managing systems can be a complex task.</span></span> <span data-ttu-id="e8b0a-126">Tools mit einer konsistenten Schnittstelle helfen, die inhärente Komplexität im Griff zu behalten.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-126">Tools that have a consistent interface help to control the inherent complexity.</span></span> <span data-ttu-id="e8b0a-127">Leider zeichnen sich Befehlszeilentools und skriptfähige COM-Objekte nicht durch ihre Konsistenz aus.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-127">Unfortunately, command-line tools and scriptable COM objects aren't known for their consistency.</span></span>

<span data-ttu-id="e8b0a-128">PowerShell besticht durch Konsistenz.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-128">The consistency of PowerShell is one of its primary assets.</span></span> <span data-ttu-id="e8b0a-129">Wenn Sie z.B. gelernt haben, wie das Cmdlet `Sort-Object` verwendet wird, können Sie mit diesem Wissen die Ausgabe sämtlicher Cmdlets sortieren.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-129">For example, if you learn how to use the `Sort-Object` cmdlet, you can use that knowledge to sort the output of any cmdlet.</span></span> <span data-ttu-id="e8b0a-130">Sie müssen also nicht für jedes Cmdlet eine andere Sortierroutine erlernen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-130">You don't have to learn the different sorting routines of each cmdlet.</span></span>

<span data-ttu-id="e8b0a-131">Darüber hinaus müssen Cmdlet-Entwickler keine Sortierfunktionen für ihre Cmdlets entwerfen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-131">Additionally, cmdlet developers don't have to design sorting features for their cmdlets.</span></span> <span data-ttu-id="e8b0a-132">PowerShell bietet ein Framework mit den grundlegenden Funktionen, das Konsistenz erzwingt.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-132">PowerShell provides a framework with the basic features that forces consistency.</span></span> <span data-ttu-id="e8b0a-133">Das Framework bietet einige Optionen nicht, die dem Entwickler überlassen werden.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-133">The framework eliminates some choices that are left to the developer.</span></span> <span data-ttu-id="e8b0a-134">Im Gegenzug vereinfacht es aber die Entwicklung von Cmdlets deutlich.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-134">But, in return, it makes the development of cmdlets much simpler.</span></span>

### <a name="interactive-and-scripting-environments"></a><span data-ttu-id="e8b0a-135">Interaktive und Skriptumgebungen</span><span class="sxs-lookup"><span data-stu-id="e8b0a-135">Interactive and scripting environments</span></span>

<span data-ttu-id="e8b0a-136">Die Windows-Eingabeaufforderung bietet eine interaktive Shell mit Zugriff auf Befehlszeilentools und grundlegende Funktionen für die Skripterstellung.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-136">The Windows Command Prompt provides an interactive shell with access to command-line tools and basic scripting.</span></span> <span data-ttu-id="e8b0a-137">Windows Script Host (WSH) weist skriptfähige Befehlszeilentools und COM-Automatisierungsobjekte auf, jedoch keine interaktive Shell.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-137">Windows Script Host (WSH) has scriptable command-line tools and COM automation objects, but doesn't provide an interactive shell.</span></span>

<span data-ttu-id="e8b0a-138">PowerShell kombiniert eine interaktive Shell und einer Skriptumgebung.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-138">PowerShell combines an interactive shell and a scripting environment.</span></span> <span data-ttu-id="e8b0a-139">PowerShell kann auf Befehlszeilentools, COM-Objekte und .NET-Klassenbibliotheken zugreifen.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-139">PowerShell can access command-line tools, COM objects, and .NET class libraries.</span></span> <span data-ttu-id="e8b0a-140">Diese Kombination von Features erweitert die Möglichkeiten von interaktiven Benutzern, Skriptautoren und Systemadministratoren.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-140">This combination of features extends the capabilities of the interactive user, the script writer, and the system administrator.</span></span>

### <a name="object-orientation"></a><span data-ttu-id="e8b0a-141">Objektorientierung</span><span class="sxs-lookup"><span data-stu-id="e8b0a-141">Object orientation</span></span>

<span data-ttu-id="e8b0a-142">PowerShell ist objekt- und nicht textbasiert.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-142">PowerShell is based on object not text.</span></span> <span data-ttu-id="e8b0a-143">Die Ausgabe eines Befehls ist ein Objekt.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-143">The output of a command is an object.</span></span> <span data-ttu-id="e8b0a-144">Sie können das Ausgabeobjekt über die Pipeline als Eingabe an einen anderen Befehl senden.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-144">You can send the output object, through the pipeline, to another command as its input.</span></span>

<span data-ttu-id="e8b0a-145">Diese Pipeline bietet Benutzern, die bereits über Erfahrung mit anderen Shells verfügen, eine vertraute Schnittstelle.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-145">This pipeline provides a familiar interface for people experienced with other shells.</span></span> <span data-ttu-id="e8b0a-146">PowerShell erweitert dieses Konzept durch das Senden von Objekten anstelle von Text.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-146">PowerShell extends this concept by sending objects rather than text.</span></span>

### <a name="easy-transition-to-scripting"></a><span data-ttu-id="e8b0a-147">Einfacher Übergang zur Skripterstellung</span><span class="sxs-lookup"><span data-stu-id="e8b0a-147">Easy transition to scripting</span></span>

<span data-ttu-id="e8b0a-148">Die Erkennbarkeit von Befehlen in PowerShell vereinfacht den Übergang von der interaktiven Eingabe von Befehlen zum Erstellen und Ausführen von Skripts.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-148">PowerShell's command discoverability makes it easy to transition from typing commands interactively to creating and running scripts.</span></span> <span data-ttu-id="e8b0a-149">Aufzeichnungen und der Verlauf von PowerShell erleichtern das Kopieren von Befehlen in eine Datei, um sie als Skript zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="e8b0a-149">PowerShell transcripts and history make it easy to copy commands to a file for use as a script.</span></span>
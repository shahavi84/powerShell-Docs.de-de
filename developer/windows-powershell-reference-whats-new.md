---
title: Windows PowerShell-Referenz – Neuigkeiten
ms.date: 09/13/2016
ms.topic: article
ms.openlocfilehash: 364d081ddf2f87ceeaa47732266a35f4a126246f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858546"
---
# <a name="whats-new"></a><span data-ttu-id="9b7be-102">Neues</span><span class="sxs-lookup"><span data-stu-id="9b7be-102">What's New</span></span>

<span data-ttu-id="9b7be-103">Windows PowerShell 2.0 bietet die folgenden neuen Features für die Verwendung, beim Schreiben von Cmdlets, Anbietern und Hosten von Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-103">Windows PowerShell 2.0 provides the following new features for use when writing cmdlets, providers, and host applications.</span></span>

## <a name="modules"></a><span data-ttu-id="9b7be-104">Module</span><span class="sxs-lookup"><span data-stu-id="9b7be-104">Modules</span></span>

<span data-ttu-id="9b7be-105">Sie können jetzt Verpacken und Verteilen von Windows PowerShell-Lösungen mithilfe von Modulen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-105">You can now package and distribute Windows PowerShell solutions by using modules.</span></span> <span data-ttu-id="9b7be-106">Module können Sie Partitionen, organisieren und abstrahieren von Ihren Windows PowerShell-Code in eigenständige, wieder verwendbaren Einheiten.</span><span class="sxs-lookup"><span data-stu-id="9b7be-106">Modules allow you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="9b7be-107">Weitere Informationen zu Modulen finden Sie in das Schreiben eines Windows PowerShell-Moduls.</span><span class="sxs-lookup"><span data-stu-id="9b7be-107">For more information about modules, see Writing a Windows PowerShell Module.</span></span>

## <a name="the-powershell-class"></a><span data-ttu-id="9b7be-108">Die PowerShell-Klasse</span><span class="sxs-lookup"><span data-stu-id="9b7be-108">The PowerShell class</span></span>

<span data-ttu-id="9b7be-109">Die PowerShell-Klasse bietet es sich um eine einfachere Lösung zum Erstellen von Anwendungen, die als hostanwendungen, die Befehle programmgesteuert ausführen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-109">The PowerShell class provides a simpler solution for creating applications, referred to as host applications, that programmatically run commands.</span></span> <span data-ttu-id="9b7be-110">Diese Klasse können Sie zum Erstellen einer Pipeline von Befehlen geben den Runspace, der verwendet wird, um die Befehle auszuführen, und geben Sie die Befehle aufrufen, synchron oder asynchron.</span><span class="sxs-lookup"><span data-stu-id="9b7be-110">This class allows you to create a pipeline of commands, specify the runspace that is used to run the commands, and specify invoking the commands synchronously or asynchronously.</span></span>

## <a name="the-runspacepool-class"></a><span data-ttu-id="9b7be-111">Die RunspacePool-Klasse</span><span class="sxs-lookup"><span data-stu-id="9b7be-111">The RunspacePool class</span></span>

<span data-ttu-id="9b7be-112">Runspace-Pools können Sie mehreren Runspaces mithilfe eines einzelnen Aufrufs zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-112">Runspace pools allow you to create multiple runspaces by using a single call.</span></span> <span data-ttu-id="9b7be-113">Die Methode CreateRunspacePool bietet mehrere Überladungen, die zum Erstellen von Runspaces, die die gleichen Funktionen, z. B. die gleichen Host, den anfänglichen Sitzungsstatus und die Verbindungsinformationen verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-113">The CreateRunspacePool method provides several overloads that can be used to create runspaces that have the same features, such as the same host, initial session state, and connection information.</span></span>

## <a name="the-initialsessionstate-class"></a><span data-ttu-id="9b7be-114">Die InitialSessionState-Klasse</span><span class="sxs-lookup"><span data-stu-id="9b7be-114">The InitialSessionState class</span></span>

<span data-ttu-id="9b7be-115">Die InitialSessionState-Klasse können Sie eine Status-Sitzungskonfiguration zu erstellen, die verwendet wird, wenn ein Runspace geöffnet wird.</span><span class="sxs-lookup"><span data-stu-id="9b7be-115">The InitialSessionState class allows you to create a session state configuration that is used when a runspace is opened.</span></span> <span data-ttu-id="9b7be-116">Sie können eine benutzerdefinierte Konfiguration verwenden, eine Standardkonfiguration, die die Befehlen Mshshort enthält und eine Konfiguration, dessen Befehle beschränkt sind, basierend auf den Funktionen der Sitzung, zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-116">You can create a custom configuration, a default configuration that includes the commands provided by mshshort, and a configuration whose commands are restricted based on the capabilities of the session.</span></span>

## <a name="remote-runspaces"></a><span data-ttu-id="9b7be-117">Remote runspaces</span><span class="sxs-lookup"><span data-stu-id="9b7be-117">Remote runspaces</span></span>

<span data-ttu-id="9b7be-118">Sie können jetzt erstellen Runspaces, die geöffnet werden, können auf den Remotecomputern können Sie auf dem Remotecomputer Befehle ausführen und die Ergebnisse lokal erfassen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-118">You can now create runspaces that can be opened on remote computers, allowing you to run commands on the remote machine and collect the results locally.</span></span> <span data-ttu-id="9b7be-119">Um einen Remoterunspace erstellen zu können, müssen Sie Informationen über die Remoteverbindung angeben, wenn den Runspace zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-119">To create a remote runspace, you must specify information about the remote connection when creating the runspace.</span></span> <span data-ttu-id="9b7be-120">Siehe Beispiele für die CreateRunspace und CreateRunspacePool-Methoden.</span><span class="sxs-lookup"><span data-stu-id="9b7be-120">See the CreateRunspace and CreateRunspacePool methods for examples.</span></span> <span data-ttu-id="9b7be-121">Informationen für die Verbindung wird durch die RunspaceConnectionInfo-Klasse definiert.</span><span class="sxs-lookup"><span data-stu-id="9b7be-121">The connection information is defined by the RunspaceConnectionInfo class.</span></span>

## <a name="private-runspace-elements"></a><span data-ttu-id="9b7be-122">Private Runspace-Elemente</span><span class="sxs-lookup"><span data-stu-id="9b7be-122">Private runspace elements</span></span>

<span data-ttu-id="9b7be-123">Sie können jetzt Runspaces erstellen, dessen Elemente öffentlich oder privat sind.</span><span class="sxs-lookup"><span data-stu-id="9b7be-123">You can now create runspaces whose elements are public or private.</span></span> <span data-ttu-id="9b7be-124">Dadurch können Sie zum Erstellen von Runspaces, dessen Elemente mit dem Runspace verfügbar sind, jedoch sind nicht für den Benutzer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9b7be-124">This allows you to create runspaces whose elements are available to the runspace, but are not available to the user.</span></span> <span data-ttu-id="9b7be-125">Finden Sie unter der ConstrainedSessionStateEntry-Klasse, um herauszufinden, welche Elemente der Runspace private vorgenommen werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-125">See the ConstrainedSessionStateEntry class to find out which elements of the runspace can be made private.</span></span>

## <a name="runspace-threading-modes-and-apartment-state"></a><span data-ttu-id="9b7be-126">Threading-Modi und Apartmentzustand Runspace</span><span class="sxs-lookup"><span data-stu-id="9b7be-126">Runspace threading modes and apartment state</span></span>

<span data-ttu-id="9b7be-127">Sie können jetzt angeben, wie Threads erstellt und verwendet werden, beim Ausführen der Befehle in einem Runspace.</span><span class="sxs-lookup"><span data-stu-id="9b7be-127">You can now specify how threads are created and used when running commands in a runspace.</span></span> <span data-ttu-id="9b7be-128">Siehe die System.Management.Automation.Runspaces.Runspace.ThreadOptions und System.Management.Automation.Runspaces.RunspacePool.ThreadOptions.</span><span class="sxs-lookup"><span data-stu-id="9b7be-128">See the System.Management.Automation.Runspaces.Runspace.ThreadOptions and System.Management.Automation.Runspaces.RunspacePool.ThreadOptions properties.</span></span>

<span data-ttu-id="9b7be-129">Sie erhalten nun den Apartmentzustand des Threads, die zum Ausführen von Befehlen in einem Runspace verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9b7be-129">You can now get the apartment state of the threads that are used to run commands in a runspace.</span></span> <span data-ttu-id="9b7be-130">Siehe die System.Management.Automation.Runspaces.Runspace.ApartmentState und System.Management.Automation.Runspaces.RunspacePool.ApartmentState.</span><span class="sxs-lookup"><span data-stu-id="9b7be-130">See the System.Management.Automation.Runspaces.Runspace.ApartmentState and System.Management.Automation.Runspaces.RunspacePool.ApartmentState properties.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="9b7be-131">Transaktions-cmdlets</span><span class="sxs-lookup"><span data-stu-id="9b7be-131">Transaction cmdlets</span></span>

<span data-ttu-id="9b7be-132">Sie können nun Cmdlets erstellen, die innerhalb einer Transaktion verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-132">You can now create cmdlets that can be used within a transaction.</span></span> <span data-ttu-id="9b7be-133">Wenn ein Cmdlet in einer Transaktion verwendet wird, die Aktionen sind temporär, und sie akzeptiert oder abgelehnt wird, durch die Transaktions-Cmdlets von Windows PowerShell bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-133">When a cmdlet is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="9b7be-134">Weitere Informationen über Transaktionen finden Sie unter Vorgehensweise unterstützen Transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-134">For more information about transactions, see How to Support Transactions.</span></span>

## <a name="transaction-provider"></a><span data-ttu-id="9b7be-135">Transaction-Anbieter</span><span class="sxs-lookup"><span data-stu-id="9b7be-135">Transaction provider</span></span>

<span data-ttu-id="9b7be-136">Sie können jetzt Anbieter erstellen, die innerhalb einer Transaktion verwendet werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-136">You can now create providers that can be used within a transaction.</span></span> <span data-ttu-id="9b7be-137">Ähnlich wie bei Cmdlets, wenn ein Anbieter in einer Transaktion verwendet wird, die Aktionen sind temporär, und sie akzeptiert oder abgelehnt wird, durch die Transaktions-Cmdlets von Windows PowerShell bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-137">Similar to cmdlets, when a provider is used in a transaction, its actions are temporary, and they can be accepted or rejected by the transaction cmdlets provided by Windows PowerShell.</span></span>

<span data-ttu-id="9b7be-138">Weitere Informationen zum Angeben von Unterstützung für die Transaktion innerhalb einer Klasse finden Sie unter der System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="9b7be-138">For more information about specifying support for transaction within a provider class, see the System.Management.Automation.Provider.CmdletProviderAttribute.ProviderCapabilities property.</span></span>

## <a name="job-cmdlets"></a><span data-ttu-id="9b7be-139">Job-cmdlets</span><span class="sxs-lookup"><span data-stu-id="9b7be-139">Job cmdlets</span></span>

<span data-ttu-id="9b7be-140">Sie können nun die Cmdlets schreiben, die ihre Aktionen als Auftrag ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-140">You can now write cmdlets that can perform their action as a job.</span></span> <span data-ttu-id="9b7be-141">Diese Aufträge werden im Hintergrund ohne Interaktion mit der aktuellen Sitzung ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="9b7be-141">These jobs are run in the background without interacting with the current session.</span></span> <span data-ttu-id="9b7be-142">Weitere Informationen dazu, wie das Windows PowerShell-Aufträge unterstützt finden Sie unter Hintergrundaufträge.</span><span class="sxs-lookup"><span data-stu-id="9b7be-142">For more information about how Windows PowerShell supports jobs, see Background Jobs.</span></span>

## <a name="cmdlet-output-types"></a><span data-ttu-id="9b7be-143">Cmdlet-Ausgabetypen</span><span class="sxs-lookup"><span data-stu-id="9b7be-143">Cmdlet output types</span></span>

<span data-ttu-id="9b7be-144">Sie können jetzt .NET Framework-Typen angeben, die durch Ihre Cmdlets zurückgegeben werden, durch die OutputType-Attribut deklarieren, wenn Ihre Cmdlets schreiben.</span><span class="sxs-lookup"><span data-stu-id="9b7be-144">You can now specify the .NET Framework types that are returned by your cmdlets by declaring the OutputType attribute when writing your cmdlets.</span></span> <span data-ttu-id="9b7be-145">Dadurch können andere Benutzer zu bestimmen, welche Art von Objekten von einem Cmdlet zurückgegeben werden, anhand der OutputType-Eigenschaft des-Cmdlets.</span><span class="sxs-lookup"><span data-stu-id="9b7be-145">This will allow others to determine what type of objects are returned by a cmdlet by looking at the OutputType property of the cmdlet.</span></span>

## <a name="event-support"></a><span data-ttu-id="9b7be-146">Ereignisunterstützung</span><span class="sxs-lookup"><span data-stu-id="9b7be-146">Event support</span></span>

<span data-ttu-id="9b7be-147">Sie können nun die Cmdlets schreiben, die Nutzung von Ereignissen und hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-147">You can now write cmdlets that add and consume events.</span></span> <span data-ttu-id="9b7be-148">Siehe PSEvent-Klasse.</span><span class="sxs-lookup"><span data-stu-id="9b7be-148">See the PSEvent class.</span></span>

## <a name="proxy-commands"></a><span data-ttu-id="9b7be-149">Proxy-Befehle</span><span class="sxs-lookup"><span data-stu-id="9b7be-149">Proxy commands</span></span>

<span data-ttu-id="9b7be-150">Sie können nun die Proxy-Befehle schreiben, mit denen ein anderer Befehl ausgeführt werden können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-150">You can now write proxy commands that can be used to run another command.</span></span> <span data-ttu-id="9b7be-151">Ein Proxybefehl können Sie steuern, welche Funktion des Quell-Cmdlets für den Benutzer verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="9b7be-151">A proxy command allows you to control what functionality of the source cmdlet is available to the user.</span></span> <span data-ttu-id="9b7be-152">Beispielsweise können Sie einen Proxybefehl erstellen, der einen Parameter entfernt, der durch den Befehl "Quelle" bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="9b7be-152">For example, you can create a proxy command that removes a parameter that is supplied by the source command.</span></span> <span data-ttu-id="9b7be-153">Siehe ProxyCommand-Klasse.</span><span class="sxs-lookup"><span data-stu-id="9b7be-153">See the ProxyCommand class.</span></span>

## <a name="multiple-choice-prompts"></a><span data-ttu-id="9b7be-154">Mehrere aufforderungen der Auswahl</span><span class="sxs-lookup"><span data-stu-id="9b7be-154">Multiple choice prompts</span></span>

<span data-ttu-id="9b7be-155">Sie können nun Anwendungen schreiben, die Anweisungen bereitstellen können, mit die den Benutzer mehrere Optionen auswählen können.</span><span class="sxs-lookup"><span data-stu-id="9b7be-155">You can now write applications that can provide prompts that allow the user to select multiple choices.</span></span> <span data-ttu-id="9b7be-156">Sehen Sie die IHostUISupportsMultipleChoiceSelection-Benutzeroberfläche</span><span class="sxs-lookup"><span data-stu-id="9b7be-156">See the IHostUISupportsMultipleChoiceSelection interface</span></span>

## <a name="interactive-sessions"></a><span data-ttu-id="9b7be-157">Interaktive Sitzungen</span><span class="sxs-lookup"><span data-stu-id="9b7be-157">Interactive sessions</span></span>

<span data-ttu-id="9b7be-158">Sie können nun Anwendungen schreiben, die gestartet oder beendet eine interaktive Sitzung auf einem Remotecomputer befindet.</span><span class="sxs-lookup"><span data-stu-id="9b7be-158">You can now write applications that can start and stop an interactive session on a remote computer.</span></span>
<span data-ttu-id="9b7be-159">Sehen Sie die IHostSupportsInteractiveSession-Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="9b7be-159">See the IHostSupportsInteractiveSession interface.</span></span>

## <a name="custom-cmdlet-help-for-providers"></a><span data-ttu-id="9b7be-160">Benutzerdefinierte Cmdlet-Hilfe für Anbieter</span><span class="sxs-lookup"><span data-stu-id="9b7be-160">Custom Cmdlet Help for Providers</span></span>

<span data-ttu-id="9b7be-161">Sie können jetzt benutzerdefinierte Hilfethemen für die Anbieter-Cmdlets erstellen.</span><span class="sxs-lookup"><span data-stu-id="9b7be-161">You can now create customized Help topics for the provider cmdlets.</span></span> <span data-ttu-id="9b7be-162">Benutzerdefinierte Cmdlet-Hilfethemen können erklären, wie das Cmdlet funktioniert in der Anbieter Pfad und Dokument spezielle Features, einschließlich der dynamische Parameter, die der Anbieter das-Cmdlet hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="9b7be-162">Custom cmdlet help topics can explain how the cmdlet works in the provider path and document special features, including the dynamic parameters that the provider adds to the cmdlet.</span></span>
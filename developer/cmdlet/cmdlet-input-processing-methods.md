---
title: -Cmdlet Eingabeverarbeitungsmethoden | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- virtual methods (PowerShell SDK]
ms.assetid: b0bb8172-c9fa-454b-9f1b-57c3fe60671b
caps.latest.revision: 12
ms.openlocfilehash: 065214647dfa6d376b727930fe75140911095faf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059370"
---
# <a name="cmdlet-input-processing-methods"></a><span data-ttu-id="f2f5c-102">Cmdlet-Eingabeverarbeitungsmethoden</span><span class="sxs-lookup"><span data-stu-id="f2f5c-102">Cmdlet Input Processing Methods</span></span>

<span data-ttu-id="f2f5c-103">Cmdlets muss es sich um eine oder mehrere der in diesem Thema für ihre Arbeit beschriebenen eingabeverarbeitungsmethoden überschreiben.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-103">Cmdlets must override one or more of the input processing methods described in this topic to perform their work.</span></span> <span data-ttu-id="f2f5c-104">Diese Methoden ermöglichen das-Cmdlet zum Ausführen von vorab verarbeitete Vorgänge, die Eingabe verarbeitet und nach der Verarbeitung von Vorgängen.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-104">These methods allow the cmdlet to perform pre-processing operations, input processing operations, and post-processing operations.</span></span> <span data-ttu-id="f2f5c-105">Diese Methoden ermöglichen auch das Cmdlet-Verarbeitung zu beenden.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-105">These methods also allow you to stop cmdlet processing.</span></span>

## <a name="pre-processing-tasks"></a><span data-ttu-id="f2f5c-106">Vorab verarbeitete Tasks</span><span class="sxs-lookup"><span data-stu-id="f2f5c-106">Pre-Processing Tasks</span></span>

<span data-ttu-id="f2f5c-107">Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) Methode, um alle vorverarbeitungsoperationen hinzuzufügen, die für alle Datensätze gültig sind, die später vom Cmdlet verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-107">Cmdlets should override the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to add any preprocessing operations that are valid for all the records that will be processed later by the cmdlet.</span></span> <span data-ttu-id="f2f5c-108">Wenn Windows PowerShell über eine Befehlspipeline verarbeitet, ruft Windows PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-108">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="f2f5c-109">Weitere Informationen dazu, wie Windows PowerShell den Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f2f5c-109">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f2f5c-110">Der folgende Code zeigt eine Implementierung der [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) Methode.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-110">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void BeginProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the BeginProcessing template."
  WriteObject("This is a test of the BeginProcessing template.");
}
```

<span data-ttu-id="f2f5c-111">Ein ausführlicheres Beispiel zur Verwendung der [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) -Methode finden Sie unter [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f2f5c-111">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span> <span data-ttu-id="f2f5c-112">In diesem Tutorial die **Select-Str** Cmdlet verwendet die [System.Management.Automation.Cmdlet.Beginprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) Methode, um den regulären Ausdruck zu generieren, die verwendet wird, um die Eingabe, die Datensätze verarbeitet werden zu suchen.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-112">In this tutorial, the **Select-Str** cmdlet uses the [System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0) method to generate the regular expression that is used to search the input processing records.</span></span>

## <a name="input-processing-tasks"></a><span data-ttu-id="f2f5c-113">Geben Sie die Verarbeitung von Aufgaben</span><span class="sxs-lookup"><span data-stu-id="f2f5c-113">Input Processing Tasks</span></span>

<span data-ttu-id="f2f5c-114">Cmdlets können außer Kraft setzen der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) Methode, um die Eingabe zu verarbeiten, die an das-Cmdlet gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-114">Cmdlets can override the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method to process the input that is sent to the cmdlet.</span></span> <span data-ttu-id="f2f5c-115">Wenn Windows PowerShell über eine Befehlspipeline verarbeitet, ruft Windows PowerShell diese Methode für jeden Eingabedatensatz, die vom Cmdlet verarbeitet wird.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-115">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method for each input record that is processed by the cmdlet.</span></span> <span data-ttu-id="f2f5c-116">Weitere Informationen dazu, wie Windows PowerShell den Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f2f5c-116">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f2f5c-117">Der folgende Code zeigt eine Implementierung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) Methode.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-117">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void ProcessRecord()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the ProcessRecord template."
  WriteObject("This is a test of the ProcessRecord template.");
}
```

<span data-ttu-id="f2f5c-118">Ein ausführlicheres Beispiel zur Verwendung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) -Methode finden Sie unter [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f2f5c-118">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="post-processing-tasks"></a><span data-ttu-id="f2f5c-119">Nach der Verarbeitung von Aufgaben</span><span class="sxs-lookup"><span data-stu-id="f2f5c-119">Post-Processing Tasks</span></span>

<span data-ttu-id="f2f5c-120">Cmdlets sollten außer Kraft setzen der [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) Methode, um alle nachträglich verarbeiteten Vorgänge hinzuzufügen, die für alle Datensätze gültig sind, die vom Cmdlet verarbeitet wurden.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-120">Cmdlets should override the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method to add any post-processing operations that are valid for all the records that were processed by the cmdlet.</span></span> <span data-ttu-id="f2f5c-121">Z. B. Ihr Cmdlet möglicherweise Objektvariablen bereinigen, wenn der Prozess beendet wird verarbeitet.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-121">For example, your cmdlet might have to clean up object variables after it is finished processing.</span></span>

<span data-ttu-id="f2f5c-122">Wenn Windows PowerShell über eine Befehlspipeline verarbeitet, ruft Windows PowerShell diese Methode einmal für jede Instanz des-Cmdlets in der Pipeline.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-122">When Windows PowerShell processes a command pipeline, Windows PowerShell calls this method once for each instance of the cmdlet in the pipeline.</span></span> <span data-ttu-id="f2f5c-123">Allerdings ist es wichtig zu beachten, dass die Windows PowerShell-Laufzeit nicht Ruft die [System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) Methode, wenn das-Cmdlet über die Verarbeitung von Benutzereingaben Zielpfads abgebrochen wird oder wenn ein Abbruch tritt Fehler in einem beliebigen Teil des Cmdlets auf.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-123">However, it is important to remember that the Windows PowerShell runtime will not call the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) method if the cmdlet is canceled midway through its input processing or if a terminating error occurs in any part of the cmdlet.</span></span> <span data-ttu-id="f2f5c-124">Aus diesem Grund sollte ein Cmdlet, das Objekt Bereinigung erfordert die vollständige implementieren [System.IDisposable](/dotnet/api/System.IDisposable) Muster, einschließlich von einem Finalizer, damit die Laufzeit sowohl aufrufen kann die [ System.Management.Automation.Cmdlet.Endprocessing%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) und [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) Methoden am Ende der Verarbeitung.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-124">For this reason, a cmdlet that requires object cleanup should implement the complete [System.IDisposable](/dotnet/api/System.IDisposable) pattern, including a finalizer, so that the runtime can call both the [System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0) and [System.IDisposable.Dispose\*](/dotnet/api/System.IDisposable.Dispose) methods at the end of processing.</span></span> <span data-ttu-id="f2f5c-125">Weitere Informationen dazu, wie Windows PowerShell den Befehlspipeline aufruft, finden Sie unter [Cmdlet Verarbeitung Lebenszyklus](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span><span class="sxs-lookup"><span data-stu-id="f2f5c-125">For more information about how Windows PowerShell invokes the command pipeline, see [Cmdlet Processing Lifecycle](https://msdn.microsoft.com/en-us/3202f55c-314d-4ac3-ad78-4c7ca72253c5).</span></span>

<span data-ttu-id="f2f5c-126">Der folgende Code zeigt eine Implementierung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) Methode.</span><span class="sxs-lookup"><span data-stu-id="f2f5c-126">The following code shows an implementation of the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method.</span></span>

```csharp
protected override void EndProcessing()
{
  // Replace the WriteObject method with the logic required
  // by your cmdlet. It is used here to generate the following
  // output:
  // "This is a test of the EndProcessing template."
  WriteObject("This is a test of the EndProcessing template.");
}
```

<span data-ttu-id="f2f5c-127">Ein ausführlicheres Beispiel zur Verwendung der [System.Management.Automation.Cmdlet.Processrecord%2A? Displayproperty = Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) -Methode finden Sie unter [SelectStr Tutorial](./selectstr-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="f2f5c-127">For a more detailed example of how to use the [System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0) method, see [SelectStr Tutorial](./selectstr-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2f5c-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f2f5c-128">See Also</span></span>

[<span data-ttu-id="f2f5c-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f2f5c-129">System.Management.Automation.Cmdlet.Beginprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.beginprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="f2f5c-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f2f5c-130">System.Management.Automation.Cmdlet.Processrecord%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.processrecord?view=powershellsdk-1.1.0)

[<span data-ttu-id="f2f5c-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span><span class="sxs-lookup"><span data-stu-id="f2f5c-131">System.Management.Automation.Cmdlet.Endprocessing%2A?Displayproperty=Fullname</span></span>](/dotnet/api/system.management.automation.cmdlet.endprocessing?view=powershellsdk-1.1.0)

[<span data-ttu-id="f2f5c-132">System.IDisposable</span><span class="sxs-lookup"><span data-stu-id="f2f5c-132">System.IDisposable</span></span>](/dotnet/api/System.IDisposable)

[<span data-ttu-id="f2f5c-133">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="f2f5c-133">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
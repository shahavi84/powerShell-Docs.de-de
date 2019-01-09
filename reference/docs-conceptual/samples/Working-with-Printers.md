---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Druckern
ms.assetid: 4f29ead3-f83b-4706-ac3e-f2154ff38dc5
ms.openlocfilehash: 5638629fdf79371c8eff9ee9194b642034250fff
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401967"
---
# <a name="working-with-printers"></a><span data-ttu-id="4555b-103">Arbeiten mit Druckern</span><span class="sxs-lookup"><span data-stu-id="4555b-103">Working with Printers</span></span>

<span data-ttu-id="4555b-104">Sie können Windows PowerShell zum Verwalten von Druckern mit WMI und dem COM-Objekt „WScript.Network“ vom WSH verwenden.</span><span class="sxs-lookup"><span data-stu-id="4555b-104">You can use Windows PowerShell to manage printers by using WMI and the WScript.Network COM object from WSH.</span></span> <span data-ttu-id="4555b-105">Wir werden eine Kombination beider Tools verwenden, um bestimmte Aufgaben zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="4555b-105">We will use a mix of both tools to demonstrate specific tasks.</span></span>

### <a name="listing-printer-connections"></a><span data-ttu-id="4555b-106">Auflisten von Druckerverbindungen</span><span class="sxs-lookup"><span data-stu-id="4555b-106">Listing Printer Connections</span></span>

<span data-ttu-id="4555b-107">Die einfachste Möglichkeit, die auf einem Computer installierten Drucker aufzulisten, ist die Verwendung der WMI-Klasse **Win32_Printer**:</span><span class="sxs-lookup"><span data-stu-id="4555b-107">The simplest way to list the printers installed on a computer is to use the WMI **Win32_Printer** class:</span></span>

```powershell
Get-WmiObject -Class Win32_Printer -ComputerName
```

<span data-ttu-id="4555b-108">Sie können die Drucker auch mit dem COM-Objekt **WScript.Network** auflisten, das normalerweise in WSH-Skripts verwendet wird:</span><span class="sxs-lookup"><span data-stu-id="4555b-108">You can also list the printers by using the **WScript.Network** COM object that is typically used in WSH scripts:</span></span>

```powershell
(New-Object -ComObject WScript.Network).EnumPrinterConnections()
```

<span data-ttu-id="4555b-109">Da dieser Befehl eine einfache Zeichenfolgenauflistung von Portnamen und Druckergerätenamen ohne unterscheidende Bezeichnungen zurückgibt, ist die Ausgabe nicht leicht zu interpretieren.</span><span class="sxs-lookup"><span data-stu-id="4555b-109">Because this command returns a simple string collection of port names and printer device names without any distinguishing labels, it is not easy to interpret.</span></span>

### <a name="adding-a-network-printer"></a><span data-ttu-id="4555b-110">Hinzufügen eines Netzwerkdruckers</span><span class="sxs-lookup"><span data-stu-id="4555b-110">Adding a Network Printer</span></span>

<span data-ttu-id="4555b-111">Verwenden Sie zum Hinzufügen eines neuen Netzwerkdruckers **WScript.Network**:</span><span class="sxs-lookup"><span data-stu-id="4555b-111">To add a new network printer, use **WScript.Network**:</span></span>

```powershell
(New-Object -ComObject WScript.Network).AddWindowsPrinterConnection("\\Printserver01\Xerox5")
```

### <a name="setting-a-default-printer"></a><span data-ttu-id="4555b-112">Festlegen eines Standarddruckers</span><span class="sxs-lookup"><span data-stu-id="4555b-112">Setting a Default Printer</span></span>

<span data-ttu-id="4555b-113">Um mithilfe von WMI den Standarddrucker festzulegen, suchen Sie den Drucker in der **Win32_Printer**-Sammlung, und rufen Sie dann die Methode **SetDefaultPrinter** auf:</span><span class="sxs-lookup"><span data-stu-id="4555b-113">To use WMI to set the default printer, find the printer in the **Win32_Printer** collection and then invoke the **SetDefaultPrinter** method:</span></span>

```powershell
(Get-WmiObject -ComputerName . -Class Win32_Printer -Filter "Name='HP LaserJet 5Si'").SetDefaultPrinter()
```

<span data-ttu-id="4555b-114">**WScript.Network** ist etwas einfacher zu verwenden, da es eine **SetDefaultPrinter**-Methode besitzt, die nur den Druckernamen als Argument akzeptiert:</span><span class="sxs-lookup"><span data-stu-id="4555b-114">**WScript.Network** is a little simpler to use, because it has a **SetDefaultPrinter** method that takes only the printer name as an argument:</span></span>

```powershell
(New-Object -ComObject WScript.Network).SetDefaultPrinter('HP LaserJet 5Si')
```

### <a name="removing-a-printer-connection"></a><span data-ttu-id="4555b-115">Entfernen einer Druckerverbindung</span><span class="sxs-lookup"><span data-stu-id="4555b-115">Removing a Printer Connection</span></span>

<span data-ttu-id="4555b-116">Um eine Druckerverbindung zu entfernen, verwenden Sie die Methode **WScript.Network RemovePrinterConnection**:</span><span class="sxs-lookup"><span data-stu-id="4555b-116">To remove a printer connection, use the **WScript.Network RemovePrinterConnection** method:</span></span>

```powershell
(New-Object -ComObject WScript.Network).RemovePrinterConnection("\\Printserver01\Xerox5")
```
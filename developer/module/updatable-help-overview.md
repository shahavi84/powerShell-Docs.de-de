---
title: Übersicht über die aktualisierbare Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057602"
---
# <a name="updatable-help-overview"></a><span data-ttu-id="706c0-102">Aktualisierbare Hilfeübersicht</span><span class="sxs-lookup"><span data-stu-id="706c0-102">Updatable Help Overview</span></span>

<span data-ttu-id="706c0-103">Dieses Dokument enthält eine grundlegende Einführung in die Entwurfs- und den Betrieb von Windows PowerShell aktualisierbaren Hilfefunktion.</span><span class="sxs-lookup"><span data-stu-id="706c0-103">This document provides a basic introduction to the design and operation of the Windows PowerShell Updatable Help feature.</span></span> <span data-ttu-id="706c0-104">Es dient modulautoren und andere, die Benutzer die Windows PowerShell-Hilfethemen für Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="706c0-104">It is designed for module authors and others who deliver Windows PowerShell help topics to users.</span></span>

## <a name="introduction"></a><span data-ttu-id="706c0-105">Einführung</span><span class="sxs-lookup"><span data-stu-id="706c0-105">Introduction</span></span>

<span data-ttu-id="706c0-106">Windows PowerShell-Hilfethemen sind ein wesentlicher Bestandteil der Windows PowerShell-Oberfläche.</span><span class="sxs-lookup"><span data-stu-id="706c0-106">Windows PowerShell help topics are an integral part of the Windows PowerShell experience.</span></span> <span data-ttu-id="706c0-107">Wie Windows PowerShell-Module werden die Hilfethemen ständig aktualisiert und verbessert werden, durch die Autoren und die Beiträge der Community von Windows PowerShell-Benutzer.</span><span class="sxs-lookup"><span data-stu-id="706c0-107">Like Windows PowerShell modules, help topics are continually updated and improved by the authors and by the contributions of the community of Windows PowerShell users.</span></span>

<span data-ttu-id="706c0-108">Die *aktualisierbare Hilfe* , eingeführt in Windows PowerShell 3.0 wird sichergestellt, dass Benutzer an der Eingabeaufforderung ein, auch für die integrierte Windows PowerShell-Befehle, die neuesten Versionen der Hilfethemen haben, ohne neue Module herunterzuladen oder Ausführen von Windows Update.</span><span class="sxs-lookup"><span data-stu-id="706c0-108">The *Updatable Help* feature, introduced in Windows PowerShell 3.0, ensures that users have the newest versions of help topics at the command prompt, even for built-in Windows PowerShell commands, without downloading new modules or running Windows Update.</span></span> <span data-ttu-id="706c0-109">Aktualisierbare Hilfe wird aktualisiert einfach durch Bereitstellen von Cmdlets, die die neuesten Versionen der Hilfethemen aus dem Internet herunterladen und installieren Sie sie in der richtigen Unterverzeichnisse auf dem lokalen Computer des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="706c0-109">Updatable Help makes updating simple by providing cmdlets that download the newest versions of help topics from the Internet and install them in the correct subdirectories on the user's local computer.</span></span> <span data-ttu-id="706c0-110">Selbst Benutzer, die sich hinter Firewalls befinden können die neuen Cmdlets aktualisierte Hilfe in einer internen Dateifreigabe verwenden.</span><span class="sxs-lookup"><span data-stu-id="706c0-110">Even users who are behind firewalls can use the new cmdlets to get updated help from an internal file share.</span></span>

<span data-ttu-id="706c0-111">Aktualisierbare Hilfe wird von allen Windows PowerShell-Modulen in Windows® 8 und Windows Server® 2012 vollständig unterstützt, und seine Funktionen sind für alle Autoren von Windows PowerShell-Modul verfügbar.</span><span class="sxs-lookup"><span data-stu-id="706c0-111">Updatable Help is fully supported by all Windows PowerShell modules in Windows® 8 and Windows Server® 2012, and its features are available to all Windows PowerShell module authors.</span></span> <span data-ttu-id="706c0-112">Aktualisierbare Hilfe unterstützt nur die XML-basierte Hilfedateien.</span><span class="sxs-lookup"><span data-stu-id="706c0-112">Updatable Help supports only XML-based help files.</span></span> <span data-ttu-id="706c0-113">Kommentarbasierte Hilfe wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="706c0-113">It does not support comment-based help.</span></span>

<span data-ttu-id="706c0-114">Aktualisierbare Hilfe umfasst die folgenden Funktionen.</span><span class="sxs-lookup"><span data-stu-id="706c0-114">Updatable Help includes the following features.</span></span>

- <span data-ttu-id="706c0-115">Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) -Cmdlet, das bestimmt, ob Benutzer über die neuesten Hilfedateien haben Dateien für ein Modul und, falls nicht, lädt die neuesten Hilfedateien aus dem Internet herunter, entpackt sie und installiert sie in den Unterverzeichnissen richtige Modul auf der Computer des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="706c0-115">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, which determines whether users have the newest help files for a module and, if not, downloads the newest help files from the Internet, unpacks them, and installs them in the correct module subdirectories on the user's computer.</span></span>
  <span data-ttu-id="706c0-116">Benutzer können die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet, um die neu installierte Hilfethemen sofort anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="706c0-116">Users can use the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet to view the newly-installed help topics immediately.</span></span>
  <span data-ttu-id="706c0-117">Sie müssen kein PowerShell neu zu starten.</span><span class="sxs-lookup"><span data-stu-id="706c0-117">They do not need to restart PowerShell.</span></span>

- <span data-ttu-id="706c0-118">Die [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) -Cmdlet, das die neuesten Hilfedateien lädt Dateien aus dem Internet und speichert sie in einem Dateisystemverzeichnis.</span><span class="sxs-lookup"><span data-stu-id="706c0-118">The [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet, which downloads the newest help files from the Internet and saves them in a file system directory.</span></span> <span data-ttu-id="706c0-119">Benutzer können die `Update-Help` -Cmdlet zum Abrufen von Hilfedateien aus dem Verzeichnis, und Entpacken und installieren Sie sie in den Unterverzeichnissen Modul auf dem Computer des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="706c0-119">Users can use the `Update-Help` cmdlet to get help files from the file system directory, and unpack and install them in the module subdirectories on the user's computer.</span></span> <span data-ttu-id="706c0-120">Die `Save-Help` Cmdlet wurde entwickelt, für Benutzer mit eingeschränkter oder gar keinen Internetzugriff verfügen und für Unternehmen, die Zugriff auf das Internet einschränken möchten.</span><span class="sxs-lookup"><span data-stu-id="706c0-120">The `Save-Help` cmdlet is designed for users who have limited or no Internet access and for enterprises who prefer to limit Internet access.</span></span>

- <span data-ttu-id="706c0-121">**Die Hilfe für ein Modul**.</span><span class="sxs-lookup"><span data-stu-id="706c0-121">**Help for a Module**.</span></span> <span data-ttu-id="706c0-122">Hilfedateien für ein Modul verwaltet und als Einheit bereitgestellt werden, damit Benutzer die Hilfedateien für Module Abrufen aller können, die sie verwenden.</span><span class="sxs-lookup"><span data-stu-id="706c0-122">Help files for a module are managed and delivered as a unit, so users can get all of the help files for the modules they use.</span></span> <span data-ttu-id="706c0-123">Aktualisierbare Hilfe ist nur für Module, die nicht für Windows PowerShell-Snap-ins unterstützt.</span><span class="sxs-lookup"><span data-stu-id="706c0-123">Updatable help is supported only for modules, not for Windows PowerShell snap-ins.</span></span>

- <span data-ttu-id="706c0-124">**Versionsunterstützung**.</span><span class="sxs-lookup"><span data-stu-id="706c0-124">**Version support**.</span></span> <span data-ttu-id="706c0-125">Aktualisierbare Hilfedateien verwendet vier-Position (N1. N2. N3. Versionsnummern für N4).</span><span class="sxs-lookup"><span data-stu-id="706c0-125">Updatable Help uses standard four-position (N1.N2.N3.N4) version numbers.</span></span> <span data-ttu-id="706c0-126">Aktualisierbare Hilfedateien Hilfedateien heruntergeladen, wenn die Versionsnummer der Hilfe-auf dem Computer des Benutzers Dateien (oder in der `Save-Help` Verzeichnis) ist niedriger als die Versionsnummer der Hilfedateien auf dem Speicherort im Internet.</span><span class="sxs-lookup"><span data-stu-id="706c0-126">Updatable Help downloads help files when the version number of the help files on the user's computer (or in the `Save-Help` directory) is lower than the version number of the  help files at the Internet location.</span></span>

- <span data-ttu-id="706c0-127">**Unterstützung mehrerer Sprachen**.</span><span class="sxs-lookup"><span data-stu-id="706c0-127">**Multi-language support**.</span></span> <span data-ttu-id="706c0-128">Aktualisierbare Hilfe unterstützt Modul Hilfedateien in mehreren Benutzeroberflächenkulturen.</span><span class="sxs-lookup"><span data-stu-id="706c0-128">Updatable Help supports module help files in multiple UI cultures.</span></span> <span data-ttu-id="706c0-129">Aktualisierbare Hilfedateien Dateinamen enthalten standard Sprachcodes, z. B. "En-US" und "ja-JP" und die `Update-Help` und `Save-Help` Cmdlets müssen Sie die Hilfedateien in sprachspezifischen Unterverzeichnissen des Modulverzeichnisses.</span><span class="sxs-lookup"><span data-stu-id="706c0-129">Updatable Help file names include standard language codes, such as "en-US" and "ja-JP", and the `Update-Help` and `Save-Help` cmdlets place the help files into language-specific subdirectories of the module directory.</span></span>

- <span data-ttu-id="706c0-130">**Automatisch generierte Hilfe**.</span><span class="sxs-lookup"><span data-stu-id="706c0-130">**Auto-generated help**.</span></span> <span data-ttu-id="706c0-131">Die [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Cmdlet zeigt die grundlegende Hilfe für Befehle, die keine Hilfedateien vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="706c0-131">The [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet displays basic help for commands that do not have help files.</span></span> <span data-ttu-id="706c0-132">Die automatisch generierte Hilfe umfasst die Befehlssyntax und Aliase, und Anweisungen für die Verwendung von online-Hilfe und die aktualisierbare Hilfe.</span><span class="sxs-lookup"><span data-stu-id="706c0-132">The auto-generated help includes the command syntax and aliases, and instructions for using online help and Updatable Help.</span></span>

- <span data-ttu-id="706c0-133">**Verbesserte Onlinehilfe**.</span><span class="sxs-lookup"><span data-stu-id="706c0-133">**Enhanced Online help**.</span></span> <span data-ttu-id="706c0-134">Einfacher Zugriff auf die Onlinehilfe ist die Hilfedateien mehr erforderlich.</span><span class="sxs-lookup"><span data-stu-id="706c0-134">Easy access to online help no longer requires help files.</span></span> <span data-ttu-id="706c0-135">Die **Online** Parameter, der die `Get-Help` Cmdlet ruft nun die URL von einem Onlinehilfethema aus der Wert des der **HelpUri** Eigenschaft von Befehlen, wenn die online-Hilfe-URL in einer Hilfedatei gefunden werden kann.</span><span class="sxs-lookup"><span data-stu-id="706c0-135">The **Online** parameter of the `Get-Help` cmdlet now gets the URL of an online help topic from the value of the **HelpUri** property of any command, if it cannot find the online help URL in a help file.</span></span> <span data-ttu-id="706c0-136">Sie füllen können die **HelpUri** Eigenschaft durch das Hinzufügen einer **HelpUri** -Attribut auf den Code des-Cmdlets, Funktionen und CIM-Befehle oder mithilfe der **. Link** kommentarbasierte Hilfe-Direktive in Workflows und Skripts.</span><span class="sxs-lookup"><span data-stu-id="706c0-136">You can populate the **HelpUri** property by adding a **HelpUri** attribute to the code of cmdlets, functions, and CIM commands, or by using the **.Link** comment-based help directive in workflows and scripts.</span></span>

  <span data-ttu-id="706c0-137">Um unsere Hilfedateien aktualisieren zu können, stammen nicht die Windows PowerShell-Module in Windows 8 und Windows Server vNext Hilfedateien.</span><span class="sxs-lookup"><span data-stu-id="706c0-137">To make our help files updatable, the Windows PowerShell modules in Windows 8 and Windows Server vNext do not come with help files.</span></span> <span data-ttu-id="706c0-138">Benutzer können aktualisierbare Hilfe zum Installieren von Hilfedateien und diese zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="706c0-138">Users can use Updatable Help to install help files and update them.</span></span> <span data-ttu-id="706c0-139">Autoren von anderen Modulen können Hilfedateien in Modulen enthalten, oder lassen sie.</span><span class="sxs-lookup"><span data-stu-id="706c0-139">Authors of other modules can include help files in modules or omit them.</span></span> <span data-ttu-id="706c0-140">Unterstützung für aktualisierbare Hilfe ist optional, jedoch empfohlen.</span><span class="sxs-lookup"><span data-stu-id="706c0-140">Support for Updatable Help is optional, but recommended.</span></span>
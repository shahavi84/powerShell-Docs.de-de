---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Filtern von Suchergebnissen
ms.openlocfilehash: eafbc993a37eaee7413102ef9d669a6b07d6ff6e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188807"
---
# <a name="filtering-search-results"></a><span data-ttu-id="2480f-103">Filtern von Suchergebnissen</span><span class="sxs-lookup"><span data-stu-id="2480f-103">Filtering search results</span></span>

<span data-ttu-id="2480f-104">Die Registerkarte [Elemente](https://www.powershellgallery.com/items) zeigt alle verfügbaren Elemente im PowerShell-Katalog an.</span><span class="sxs-lookup"><span data-stu-id="2480f-104">The [Items tab](https://www.powershellgallery.com/items) displays all available items in the PowerShell Gallery.</span></span>

<span data-ttu-id="2480f-105">Es gibt verschiedene Möglichkeiten, die Elemente zu filtern, zu sortieren und zu durchsuchen.</span><span class="sxs-lookup"><span data-stu-id="2480f-105">There are several ways to filter, sort, and search the items.</span></span>
<span data-ttu-id="2480f-106">Um weitere Details zu einem bestimmten Element anzuzeigen, klicken Sie auf das Element.</span><span class="sxs-lookup"><span data-stu-id="2480f-106">To see more details about a particular item, click the item.</span></span>

## <a name="filter-by"></a><span data-ttu-id="2480f-107">Filtern nach</span><span class="sxs-lookup"><span data-stu-id="2480f-107">Filter By</span></span>

<span data-ttu-id="2480f-108">Mit der Dropdownliste „Filtern nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:</span><span class="sxs-lookup"><span data-stu-id="2480f-108">The drop-down under "Filter By" allows users to filter the results by:</span></span>
- <span data-ttu-id="2480f-109">Vorabversion einbeziehen</span><span class="sxs-lookup"><span data-stu-id="2480f-109">Include Prerelease</span></span>
- <span data-ttu-id="2480f-110">Nur stabile</span><span class="sxs-lookup"><span data-stu-id="2480f-110">Stable Only</span></span>

<span data-ttu-id="2480f-111">Informationen zu „Vorabversion“ und „stabil“ finden Sie im PowerShell-Teamblog unter [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) (Versionsverwaltung von Vorabversionen zu PowerShellGet und dem PowerShell-Katalog hinzugefügt).</span><span class="sxs-lookup"><span data-stu-id="2480f-111">For information about "Prerelease" and "Stable", see [Prerelease Versioning Added to PowerShellGet and PowerShell Gallery](https://blogs.msdn.microsoft.com/powershell/2017/12/05/prerelease-versioning-added-to-powershellget-and-powershell-gallery/) in the PowerShell Team Blog.</span></span>

<span data-ttu-id="2480f-112">Mithilfe der Kontrollkästchen unter der Dropdownliste können Benutzer die Ergebnisse nach folgenden Kriterien filtern:</span><span class="sxs-lookup"><span data-stu-id="2480f-112">The checkboxes under the drop-down allow users to filter the results by:</span></span>
- <span data-ttu-id="2480f-113">Elementtypen</span><span class="sxs-lookup"><span data-stu-id="2480f-113">Item Types</span></span>
  - <span data-ttu-id="2480f-114">Modul</span><span class="sxs-lookup"><span data-stu-id="2480f-114">Module</span></span>
  - <span data-ttu-id="2480f-115">Skript</span><span class="sxs-lookup"><span data-stu-id="2480f-115">Script</span></span>
- <span data-ttu-id="2480f-116">Kategorien</span><span class="sxs-lookup"><span data-stu-id="2480f-116">Categories</span></span>
  - <span data-ttu-id="2480f-117">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="2480f-117">Cmdlet</span></span>
  - <span data-ttu-id="2480f-118">DSC-Ressource</span><span class="sxs-lookup"><span data-stu-id="2480f-118">DSC Resource</span></span>
  - <span data-ttu-id="2480f-119">Funktion</span><span class="sxs-lookup"><span data-stu-id="2480f-119">Function</span></span>
  - <span data-ttu-id="2480f-120">Rollenfunktion</span><span class="sxs-lookup"><span data-stu-id="2480f-120">Role Capability</span></span>
  - <span data-ttu-id="2480f-121">Workflow</span><span class="sxs-lookup"><span data-stu-id="2480f-121">Workflow</span></span>

<span data-ttu-id="2480f-122">Um im PowerShell-Katalog nur Module anzuzeigen, aktivieren Sie unter „Elementtypen“ die Option „Module“.</span><span class="sxs-lookup"><span data-stu-id="2480f-122">To see only modules in the PowerShell Gallery, check Module in the Item Types.</span></span>
<span data-ttu-id="2480f-123">Um im PowerShell-Katalog nur Skripts anzuzeigen, aktivieren Sie unter „Elementtypen“ die Option „Skript“.</span><span class="sxs-lookup"><span data-stu-id="2480f-123">Similarly, to see only scripts in the PowerShell Gallery, check Script in the Item Types.</span></span>

> [!NOTE]
> <span data-ttu-id="2480f-124">Filter sind inklusiv.</span><span class="sxs-lookup"><span data-stu-id="2480f-124">Filters are inclusive.</span></span>
> <span data-ttu-id="2480f-125">Beispiel: Ein Element, das sowohl Cmdlets als auch Funktionen erhält, wird angezeigt, wenn entweder „Cmdlet“ oder „Funktion“ (oder beides) aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2480f-125">Example: An item containing both cmdlets and functions will appear if either Cmdlet or Function (or both) are checked.</span></span>
> <span data-ttu-id="2480f-126">Wenn nichts davon ausgewählt ist, wird das Element nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2480f-126">If neither are selected, the item will not appear.</span></span>
> <span data-ttu-id="2480f-127">Wenn auf ähnliche Weise Kategorien ausgewählt werden, erscheinen nur Elemente, die eine dieser Kategorien enthält.</span><span class="sxs-lookup"><span data-stu-id="2480f-127">Similarly, if all categories are selected, only items containing one of those categories will appear.</span></span>
> <span data-ttu-id="2480f-128">**Elemente, die zu keiner dieser Kategorie gehören, werden nicht angezeigt.**</span><span class="sxs-lookup"><span data-stu-id="2480f-128">**Items that do not belong to any of those categories will not appear.**</span></span>

## <a name="sort-by"></a><span data-ttu-id="2480f-129">Sortieren nach</span><span class="sxs-lookup"><span data-stu-id="2480f-129">Sort By</span></span>

<span data-ttu-id="2480f-130">Mithilfe der Dropdownliste „Sortieren nach“ können Benutzer die Ergebnisse nach folgenden Kriterien filtern:</span><span class="sxs-lookup"><span data-stu-id="2480f-130">The Sort By drop-down allows users to sort the results by:</span></span>
- <span data-ttu-id="2480f-131">Beliebtheit: Die Beliebtheit wird durch die Anzahl der Downloads bestimmt.</span><span class="sxs-lookup"><span data-stu-id="2480f-131">Popularity - Popularity is determined by Download Count</span></span>
- <span data-ttu-id="2480f-132">A-Z: Alphabetisch nach Elementname.</span><span class="sxs-lookup"><span data-stu-id="2480f-132">A-Z - Alphabetically by item name</span></span>
- <span data-ttu-id="2480f-133">Aktuell: Elemente werden in der Reihenfolge der Veröffentlichungsdaten angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2480f-133">Recent - Items appear in order of publish date</span></span>

## <a name="search-box"></a><span data-ttu-id="2480f-134">Suchfeld</span><span class="sxs-lookup"><span data-stu-id="2480f-134">Search Box</span></span>

<span data-ttu-id="2480f-135">Mit dem Suchfeld können Benutzer Elemente nach Schlüsselwort suchen.</span><span class="sxs-lookup"><span data-stu-id="2480f-135">The Search Box allows users to search the items on keywords.</span></span>
<span data-ttu-id="2480f-136">Weitere Informationen finden Sie unter [Syntax für die Katalogsuche](search-syntax.md).</span><span class="sxs-lookup"><span data-stu-id="2480f-136">For more information, see [Gallery Search Syntax](search-syntax.md).</span></span>
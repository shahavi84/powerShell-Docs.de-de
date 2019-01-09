---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Sortieren von Objekten
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401187"
---
# <a name="sorting-objects"></a><span data-ttu-id="c48f3-103">Sortieren von Objekten</span><span class="sxs-lookup"><span data-stu-id="c48f3-103">Sorting Objects</span></span>

<span data-ttu-id="c48f3-104">Wir können die angezeigte Daten zu erleichtern geordnet Organisieren der `Sort-Object` Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c48f3-104">We can organize displayed data to make it easier to scan by using the `Sort-Object` cmdlet.</span></span> <span data-ttu-id="c48f3-105">`Sort-Object` erhält den Namen der eine oder mehrere Eigenschaften sortiert werden soll, und Daten, die nach den Werten dieser Eigenschaften sortiert zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="c48f3-105">`Sort-Object` takes the name of one or more properties to sort on, and returns data sorted by the values of those properties.</span></span>

## <a name="basic-sorting"></a><span data-ttu-id="c48f3-106">Grundlegende Sortierung</span><span class="sxs-lookup"><span data-stu-id="c48f3-106">Basic sorting</span></span>

<span data-ttu-id="c48f3-107">Betrachten Sie das Problem der Auflistung, Unterverzeichnisse und Dateien im aktuellen Verzeichnis.</span><span class="sxs-lookup"><span data-stu-id="c48f3-107">Consider the problem of listing subdirectories and files in the current directory.</span></span>
<span data-ttu-id="c48f3-108">Wenn Sie möchten nach zu sortieren **"LastWriteTime"** und dann nach **Namen**, können wir durch Eingabe:</span><span class="sxs-lookup"><span data-stu-id="c48f3-108">If we want to sort by **LastWriteTime** and then by **Name**, we can do it by typing:</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

<span data-ttu-id="c48f3-109">Sie können die Objekte auch in umgekehrter Reihenfolge sortieren, durch Angabe der **absteigend** switch-Parameter.</span><span class="sxs-lookup"><span data-stu-id="c48f3-109">You can also sort the objects in reverse order by specifying the **Descending** switch parameter.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a><span data-ttu-id="c48f3-110">Verwenden von Hashtabellen</span><span class="sxs-lookup"><span data-stu-id="c48f3-110">Using hash tables</span></span>

<span data-ttu-id="c48f3-111">Sie können verschiedene Eigenschaften in unterschiedlicher Reihenfolge sortieren, mithilfe von Hashtabellen in einem Array.</span><span class="sxs-lookup"><span data-stu-id="c48f3-111">You can sort different properties in different orders by using hash tables in an array.</span></span>
<span data-ttu-id="c48f3-112">Jeder Hashtabelle verwendet einen **Ausdruck** -Taste, um den Eigenschaftennamen als Zeichenfolge angeben und ein **aufsteigend** oder **absteigend** -Taste, um die Sortierreihenfolge von anzugeben `$true` oder `$false`.</span><span class="sxs-lookup"><span data-stu-id="c48f3-112">Each hash table uses an **Expression** key to specify the property name as string and an **Ascending** or **Descending** key to specify the sort order by `$true` or `$false`.</span></span>
<span data-ttu-id="c48f3-113">Die **Ausdruck** Schlüssel ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="c48f3-113">The **Expression** key is mandatory.</span></span>
<span data-ttu-id="c48f3-114">Die **aufsteigend** oder **absteigend** Schlüssel ist optional.</span><span class="sxs-lookup"><span data-stu-id="c48f3-114">The **Ascending** or **Descending** key is optional.</span></span>

<span data-ttu-id="c48f3-115">Im folgenden Beispiel werden Objekte in absteigender **"LastWriteTime"** Reihenfolge und aufsteigender **Namen** Reihenfolge.</span><span class="sxs-lookup"><span data-stu-id="c48f3-115">The following example sorts objects in descending **LastWriteTime** order and ascending **Name** order.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

<span data-ttu-id="c48f3-116">Sie können auch einen Skriptblock festlegen, um die **Ausdruck** Schlüssel.</span><span class="sxs-lookup"><span data-stu-id="c48f3-116">You can also set a scriptblock to the **Expression** key.</span></span>
<span data-ttu-id="c48f3-117">Bei der Ausführung der `Sort-Object` -Cmdlet, das "scriptblock" ausgeführt wird und das Ergebnis wird für die Sortierung verwendet.</span><span class="sxs-lookup"><span data-stu-id="c48f3-117">When running the `Sort-Object` cmdlet, the scriptblock is executed and the result is used for sorting.</span></span>

<span data-ttu-id="c48f3-118">Im folgenden Beispiel werden Objekte in absteigender Reihenfolge nach der Zeitspanne zwischen dem **CreationTime** und **"LastWriteTime"**.</span><span class="sxs-lookup"><span data-stu-id="c48f3-118">The following example sorts objects in descending order by the time span between **CreationTime** and **LastWriteTime**.</span></span>

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a><span data-ttu-id="c48f3-119">Tipps</span><span class="sxs-lookup"><span data-stu-id="c48f3-119">Tips</span></span>

<span data-ttu-id="c48f3-120">Sie können Auslassen der **Eigenschaft** Parameternamen wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c48f3-120">You can omit the **Property** parameter name as following:</span></span>

```powershell
Sort-Object LastWriteTime, Name
```

<span data-ttu-id="c48f3-121">Außerdem sehen Sie sich `Sort-Object` über den integrierten Alias `sort`:</span><span class="sxs-lookup"><span data-stu-id="c48f3-121">Besides, you can refer to `Sort-Object` by its built-in alias, `sort`:</span></span>

```powershell
sort LastWriteTime, Name
```

<span data-ttu-id="c48f3-122">Die Schlüssel in den Hashtabellen für die Sortierung können abgekürzt werden, wie folgt:</span><span class="sxs-lookup"><span data-stu-id="c48f3-122">The keys in the hash tables for sorting can be abbreviated as following:</span></span>

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

<span data-ttu-id="c48f3-123">In diesem Beispiel die **e** steht für **Ausdruck**, **d** steht für **absteigend**, und die **eine** steht für **aufsteigend**.</span><span class="sxs-lookup"><span data-stu-id="c48f3-123">In this example, the **e** stands for **Expression**, the **d** stands for **Descending**, and the **a** stands for **Ascending**.</span></span>

<span data-ttu-id="c48f3-124">Um die Lesbarkeit zu verbessern, können Sie die Hashtabellen in eine separate Variable platzieren:</span><span class="sxs-lookup"><span data-stu-id="c48f3-124">To improve readability, you can place the hash tables into a separate variable:</span></span>

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```
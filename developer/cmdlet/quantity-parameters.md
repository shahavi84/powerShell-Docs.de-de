---
title: Mengenparameter | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c0bd8a9-1749-4885-ab24-38c0a4d9f2cb
caps.latest.revision: 6
ms.openlocfilehash: 7a3efc60fcc8729d833f6de070016cfd08cc9b88
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251369"
---
# <a name="quantity-parameters"></a><span data-ttu-id="b6009-102">Mengenparameter</span><span class="sxs-lookup"><span data-stu-id="b6009-102">Quantity Parameters</span></span>

<span data-ttu-id="b6009-103">Die folgende Tabelle enthält die empfohlenen Namen und die Funktionen für Mengenparameter.</span><span class="sxs-lookup"><span data-stu-id="b6009-103">The following table lists the recommended names and functionality for quantity parameters.</span></span>

|<span data-ttu-id="b6009-104">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6009-104">Parameter</span></span>|<span data-ttu-id="b6009-105">Funktion</span><span class="sxs-lookup"><span data-stu-id="b6009-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="b6009-106">**Alle**</span><span class="sxs-lookup"><span data-stu-id="b6009-106">**All**</span></span><br><span data-ttu-id="b6009-107">Datentyp: Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="b6009-107">Data type: Boolean</span></span>|<span data-ttu-id="b6009-108">Implementieren Sie diesen Parameter, damit `true` gibt an, dass alle Ressourcen anstelle einer Standardteilmenge von Ressourcen liegende sollte.</span><span class="sxs-lookup"><span data-stu-id="b6009-108">Implement this parameter so that `true` indicates that all resources should be acted upon instead of a default subset of resources.</span></span> <span data-ttu-id="b6009-109">Implementieren Sie diesen Parameter, damit `false` gibt eine Teilmenge der Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="b6009-109">Implement this parameter so that `false` indicates a subset of the resources.</span></span>|
|<span data-ttu-id="b6009-110">**Allocation**</span><span class="sxs-lookup"><span data-stu-id="b6009-110">**Allocation**</span></span><br><span data-ttu-id="b6009-111">Datentyp: Int32</span><span class="sxs-lookup"><span data-stu-id="b6009-111">Data type: Int32</span></span>|<span data-ttu-id="b6009-112">Implementieren Sie diesen Parameter, damit der Benutzer auf die Anzahl von Elementen zuweisen angeben kann.</span><span class="sxs-lookup"><span data-stu-id="b6009-112">Implement this parameter so that the user can specify the number of items to allocate.</span></span>|
|<span data-ttu-id="b6009-113">**BlockCount**</span><span class="sxs-lookup"><span data-stu-id="b6009-113">**BlockCount**</span></span><br><span data-ttu-id="b6009-114">Datentyp: Int64</span><span class="sxs-lookup"><span data-stu-id="b6009-114">Data type: Int64</span></span>|<span data-ttu-id="b6009-115">Implementieren Sie diesen Parameter, damit der Benutzer auf die Anzahl der Block angeben kann.</span><span class="sxs-lookup"><span data-stu-id="b6009-115">Implement this parameter so that the user can specify the block count.</span></span>|
|<span data-ttu-id="b6009-116">**Count**</span><span class="sxs-lookup"><span data-stu-id="b6009-116">**Count**</span></span><br><span data-ttu-id="b6009-117">Datentyp: Int64</span><span class="sxs-lookup"><span data-stu-id="b6009-117">Data type: Int64</span></span>|<span data-ttu-id="b6009-118">Implementieren Sie diesen Parameter, damit der Benutzer auf die Anzahl die angeben kann.</span><span class="sxs-lookup"><span data-stu-id="b6009-118">Implement this parameter so that the user can specify the count.</span></span>|
|<span data-ttu-id="b6009-119">**Bereich**</span><span class="sxs-lookup"><span data-stu-id="b6009-119">**Scope**</span></span><br><span data-ttu-id="b6009-120">Datentyp: Schlüsselwort</span><span class="sxs-lookup"><span data-stu-id="b6009-120">Data type: Keyword</span></span>|<span data-ttu-id="b6009-121">Implementieren Sie diesen Parameter, damit der Benutzer den Bereich der zu verarbeitende angeben kann.</span><span class="sxs-lookup"><span data-stu-id="b6009-121">Implement this parameter so that the user can specify the scope to operate on.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b6009-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b6009-122">See Also</span></span>

[<span data-ttu-id="b6009-123">Cmdlet-Parameter</span><span class="sxs-lookup"><span data-stu-id="b6009-123">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="b6009-124">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="b6009-124">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="b6009-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b6009-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
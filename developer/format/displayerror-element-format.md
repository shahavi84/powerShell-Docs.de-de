---
title: DisplayError-Element (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 45c45800-a87d-456e-b07c-12d4d8c27c67
caps.latest.revision: 8
ms.openlocfilehash: 2c6a3d678ca68dc0d189f6ab981fdea5fef894cb
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056480"
---
# <a name="displayerror-element-format"></a><span data-ttu-id="7817d-102">Element „DisplayError“ (Format)</span><span class="sxs-lookup"><span data-stu-id="7817d-102">DisplayError Element (Format)</span></span>

<span data-ttu-id="7817d-103">Gibt an, dass die Zeichenfolge #ERR angezeigt wird, wenn ein Fehler auftritt, Anzeigen von Daten.</span><span class="sxs-lookup"><span data-stu-id="7817d-103">Specifies that the string #ERR is displayed when an error occurs displaying a piece of data.</span></span>

<span data-ttu-id="7817d-104">-Element (Format) DefaultSettings-Element (Format) DisplayError Konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="7817d-104">Configuration Element (Format) DefaultSettings Element (Format) DisplayError Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7817d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7817d-105">Syntax</span></span>

```xml
<DisplayError/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7817d-106">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="7817d-106">Attributes and Elements</span></span>

<span data-ttu-id="7817d-107">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `DisplayError` Element.</span><span class="sxs-lookup"><span data-stu-id="7817d-107">The following sections describe attributes, child elements, and the parent element of the `DisplayError` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7817d-108">Attributes</span><span class="sxs-lookup"><span data-stu-id="7817d-108">Attributes</span></span>

<span data-ttu-id="7817d-109">Keine.</span><span class="sxs-lookup"><span data-stu-id="7817d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7817d-110">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7817d-110">Child Elements</span></span>

<span data-ttu-id="7817d-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="7817d-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7817d-112">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="7817d-112">Parent Elements</span></span>

|<span data-ttu-id="7817d-113">Element</span><span class="sxs-lookup"><span data-stu-id="7817d-113">Element</span></span>|<span data-ttu-id="7817d-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7817d-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7817d-115">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7817d-115">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)|<span data-ttu-id="7817d-116">Definiert allgemeine Einstellungen, die für alle Ansichten die Formatierungsdatei gelten.</span><span class="sxs-lookup"><span data-stu-id="7817d-116">Defines common settings that apply to all the views of the formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7817d-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7817d-117">Remarks</span></span>

<span data-ttu-id="7817d-118">Standardmäßig tritt ein Fehler beim Versuch, ein Datenelement, angezeigt wird der Speicherort der Daten leer gelassen.</span><span class="sxs-lookup"><span data-stu-id="7817d-118">By default, when an error occurs while trying to display a piece of data, the location of the data is left blank.</span></span> <span data-ttu-id="7817d-119">Wenn dieses Element die #ERR-Zeichenfolge "true" festgelegt ist, wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7817d-119">When this element is set to true, the #ERR string will be displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="7817d-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7817d-120">See Also</span></span>

[<span data-ttu-id="7817d-121">DefaultSettings-Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7817d-121">DefaultSettings Element (Format)</span></span>](./defaultsettings-element-format.md)

[<span data-ttu-id="7817d-122">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="7817d-122">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
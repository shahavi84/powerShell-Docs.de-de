---
title: ItemSelectionCondition-Element für die ExpressionBinding für CustomControl (Format) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f4bea9d8-27ad-410e-ad48-287f807d3e4e
caps.latest.revision: 7
ms.openlocfilehash: 18b0113c9b7b0895a1093cb0b56cd2d02c74a6c1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858186"
---
# <a name="itemselectioncondition-element-for-expressionbinding-for-customcontrol-format"></a><span data-ttu-id="52265-102">Element „ItemSelectionCondition“ für ExpressionBinding für CustomControl (Format)</span><span class="sxs-lookup"><span data-stu-id="52265-102">ItemSelectionCondition Element for ExpressionBinding for CustomControl (Format)</span></span>

<span data-ttu-id="52265-103">Definiert die Bedingung, die für dieses Steuerelement verwendet werden, vorhanden sein muss.</span><span class="sxs-lookup"><span data-stu-id="52265-103">Defines the condition that must exist for this control to be used.</span></span> <span data-ttu-id="52265-104">Es gibt keine Beschränkung der Anzahl der auswahlbedingungen, die für ein Steuerelement ein Element angegeben werden können.</span><span class="sxs-lookup"><span data-stu-id="52265-104">There is no limit to the number of selection conditions that can be specified for a control item.</span></span> <span data-ttu-id="52265-105">Dieses Element wird verwendet, bei der Definition einer benutzerdefinierten anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="52265-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="52265-106">-Element (Format) ViewDefinitions-Element (Format) anzeigen (Format)-Element CustomControl-Element (Format) CustomEntries Konfigurationselement für CustomControl für Ansicht (Format) CustomEntry-Element für CustomEntries für Ansicht (Format) CustomItem-Element für CustomEntry für Ansicht (Format) ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format) ItemSelectionCondition-Element für Ausdrucksbindung für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="52265-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format) ExpressionBinding Element for CustomItem for CustomControl for View (Format) ItemSelectionCondition Element for Expression Binding for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="52265-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="52265-107">Syntax</span></span>

```xml
<ItemSelectionCondition>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</ItemSelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="52265-108">Attribute und Elemente</span><span class="sxs-lookup"><span data-stu-id="52265-108">Attributes and Elements</span></span>

<span data-ttu-id="52265-109">Den folgenden Abschnitten werden Attribute, untergeordnete Elemente und das übergeordnete Element des der `ItemSelectionCondition` Element.</span><span class="sxs-lookup"><span data-stu-id="52265-109">The following sections describe attributes, child elements, and the parent element of the `ItemSelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="52265-110">Attributes</span><span class="sxs-lookup"><span data-stu-id="52265-110">Attributes</span></span>

<span data-ttu-id="52265-111">Keine.</span><span class="sxs-lookup"><span data-stu-id="52265-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="52265-112">Untergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="52265-112">Child Elements</span></span>

|<span data-ttu-id="52265-113">Element</span><span class="sxs-lookup"><span data-stu-id="52265-113">Element</span></span>|<span data-ttu-id="52265-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="52265-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52265-115">PropertyName-Element für ItemSelectionCondition für CustomControl für Ansicht (Format</span><span class="sxs-lookup"><span data-stu-id="52265-115">PropertyName Element for ItemSelectionCondition for CustomControl for View (Format</span></span>](./propertyname-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="52265-116">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="52265-116">Optional element.</span></span><br /><br /> <span data-ttu-id="52265-117">Gibt die .NET-Eigenschaft, die die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="52265-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="52265-118">ScriptBlock-Element für ItemSelectionCondition für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="52265-118">ScriptBlock Element for ItemSelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-itemselectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="52265-119">Optionales Element.</span><span class="sxs-lookup"><span data-stu-id="52265-119">Optional element.</span></span><br /><br /> <span data-ttu-id="52265-120">Gibt das Skript an, das die Bedingung auslöst.</span><span class="sxs-lookup"><span data-stu-id="52265-120">Specifies the script that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="52265-121">Übergeordnete Elemente</span><span class="sxs-lookup"><span data-stu-id="52265-121">Parent Elements</span></span>

|<span data-ttu-id="52265-122">Element</span><span class="sxs-lookup"><span data-stu-id="52265-122">Element</span></span>|<span data-ttu-id="52265-123">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="52265-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="52265-124">ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="52265-124">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="52265-125">Definiert die Daten, die vom Steuerelement angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="52265-125">Defines the data that is displayed by the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="52265-126">Hinweise</span><span class="sxs-lookup"><span data-stu-id="52265-126">Remarks</span></span>

<span data-ttu-id="52265-127">Sie können einen Eigenschaftennamen oder ein Skript für diese Bedingung angeben, aber nicht beides angeben.</span><span class="sxs-lookup"><span data-stu-id="52265-127">You can specify one property name or a script for this condition but cannot specify both.</span></span>

## <a name="see-also"></a><span data-ttu-id="52265-128">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="52265-128">See Also</span></span>

[<span data-ttu-id="52265-129">Schreiben Sie eine Formatierungsdatei PowerShell</span><span class="sxs-lookup"><span data-stu-id="52265-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)

[<span data-ttu-id="52265-130">ExpressionBinding-Element für CustomItem für CustomControl für Ansicht (Format)</span><span class="sxs-lookup"><span data-stu-id="52265-130">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)
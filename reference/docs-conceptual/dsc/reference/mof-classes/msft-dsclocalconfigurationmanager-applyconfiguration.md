---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration-Methode
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953457"
---
# <a name="applyconfiguration-method"></a>ApplyConfiguration-Methode

Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden.

Wenn keine ausstehende Konfiguration vorhanden ist, wendet diese Methode die aktuelle Konfiguration erneut an.

## <a name="syntax"></a>Syntax

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parameter

*force* \[in\] Wenn dies **true** ist, wird die aktuelle Konfiguration erneut angewendet, selbst wenn eine Konfiguration aussteht.

## <a name="return-value"></a>Rückgabewert

Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.

## <a name="remarks"></a>Hinweise

Dies ist eine statische Methode.

## <a name="requirements"></a>Anforderungen

**MOF:** DscCore.mof

**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Siehe auch

[**MSFT_DSCLocalConfigurationManager-Klasse**](msft-dsclocalconfigurationmanager.md)
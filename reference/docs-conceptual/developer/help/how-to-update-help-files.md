---
title: Vorgehensweise beim Aktualisieren von Hilfedateien | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 495869a6-080e-4401-9ddc-16edd2f86857
caps.latest.revision: 6
ms.openlocfilehash: 35b3fd696419d0135fd6f662223e6c8586df443a
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811649"
---
# <a name="how-to-update-help-files"></a>Aktualisieren von Hilfedateien

In diesem Thema wird erläutert, wie Sie Hilfedateien für ein Modul aktualisieren, das aktualisierbare Hilfe unterstützt.

## <a name="updating-help-files"></a>Aktualisieren von Hilfedateien

Es gibt viele Gründe, Hilfedateien zu aktualisieren, wie z. b. das Beheben von Fehlern, das verdeutlichen eines Konzepts, das Beantworten einer häufig gestellten Frage, das Hinzufügen neuer Dateien oder das Hinzufügen neuer und besserer Beispiele.

So aktualisieren Sie eine Hilfedatei:

1. Ändern Sie die Dateien.

2. Übersetzen Sie die Dateien in andere Benutzeroberflächen Kulturen.

3. Sammeln Sie alle Hilfedateien (neu, geändert und unverändert) für das Modul in jeder Benutzeroberflächen Kultur.

4. Überprüfen Sie die Dateien anhand des XML-Schemas.

5. Erstellen Sie die CAB-Dateien für jede Benutzeroberflächen Kultur neu.

6. Erhöhen Sie in der helpinfo-XML-Datei die Versionsnummern der CAB-Datei für jede Benutzeroberflächen Kultur.

7. Laden Sie die neuen CAB-Dateien an den Speicherort hoch, der durch den Wert des **helpcontenturi** -Elements in der helpinfo-XML-Datei angegeben wird. Ersetzen Sie die älteren CAB-Dateien durch die neuen CAB-Dateien.

8. Laden Sie die aktualisierte helpinfo-XML-Datei an den Speicherort hoch, der durch den **helpinfouri** -Schlüssel im Modul Manifest angegeben wird. Ersetzen Sie die ältere helpinfo-XML-Datei durch die neue Datei.

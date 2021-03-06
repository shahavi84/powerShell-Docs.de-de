---
title: Erstellen eines Workflows mit Windows PowerShell-Aktivitäten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 12b0b246b78142f3811f9f566cd94e4dabd40cc9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557464"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a>Erstellen eines Workflows mit Windows PowerShell-Aktivitäten

Sie können einen Windows PowerShell-Workflow erstellen, indem Sie Aktivitäten aus der Visual Studio-Toolbox auswählen und Sie in das Workflow-Designer Fenster ziehen. Weitere Informationen zum Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox finden Sie unter [Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).

In den folgenden Prozeduren wird beschrieben, wie ein Workflow erstellt wird, der den Domänen Status einer Gruppe von benutzerdefinierten Computern überprüft, Sie einer Domäne zuschließt, wenn Sie noch nicht verknüpft sind, und den Status dann erneut überprüft.

### <a name="setting-up-the-project"></a>Einrichten des Projekts

1. Befolgen Sie das Verfahren unter [Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) , um ein Workflow Projekt zu erstellen und die Aktivitäten aus den Assemblys [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) und [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) der Toolbox hinzuzufügen.

2. Fügen Sie "System. Management. Automation", "Microsoft. PowerShell. Activities", "System. Management", "Microsoft. PowerShell. Management. Activities" und "Microsoft. PowerShell. Commands. Management" als Verweisassemblys zum Projekt hinzu.

### <a name="adding-activities-to-the-workflow"></a>Hinzufügen von Aktivitäten zum Workflow

1. Fügen Sie dem Workflow eine **Sequence** -Aktivität hinzu.

2. Erstellen Sie ein Argument `ComputerName` mit dem Namen und dem Argumenttyp `String[]` . Dieses Argument stellt die Namen der Computer dar, die überprüft und verknüpft werden sollen.

3. Erstellen Sie ein Argument `DomainCred` vom Typ " [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)". Dieses Argument stellt die Domänen Anmelde Informationen eines Domänen Kontos dar, das zum Hinzufügen eines Computers zur Domäne autorisiert ist.

4. Erstellen Sie ein Argument `MachineCred` vom Typ " [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)". Dieses Argument stellt die Anmelde Informationen eines Administrators auf den Computern dar, die überprüft und verknüpft werden sollen.

5. Fügen Sie eine **ParallelForEach** -Aktivität in der **Sequence** -Aktivität hinzu. Geben Sie `comp` und `ComputerName` in die Textfelder ein, sodass die Schleife die Elemente des Arrays durchläuft `ComputerName` .

6. Fügen Sie dem Text der **ParallelForEach** -Aktivität eine **Sequence** -Aktivität hinzu. Legen Sie die **Display Name** -Eigenschaft der Sequenz auf fest `JoinDomain` .

7. Fügen Sie der **JoinDomain** -Sequenz eine **getwmiobject** -Aktivität hinzu.

8. Bearbeiten Sie die Eigenschaften der **getwmiobject** -Aktivität wie folgt.

   |Eigenschaft|Value|
   |--------------|-----------|
   |**Class**|"Win32_ComputerSystem"|
   |**PSComputerName**|zuschreiben|
   |**PSCredential**|Machinecred|

9. Fügen Sie der **JoinDomain** -Sequenz nach der **getwmiobject** -Aktivität eine **addcomputer** -Aktivität hinzu.

10. Bearbeiten Sie die Eigenschaften der **addcomputer** -Aktivität wie folgt.

    |Eigenschaft|Value|
    |--------------|-----------|
    |**Computername**|zuschreiben|
    |**DomainCredential**|Domaincred|

11. Fügen Sie der **JoinDomain** -Sequenz nach der **addcomputer** -Aktivität eine **restartcomputer** -Aktivität hinzu.

12. Bearbeiten Sie die Eigenschaften der **restartcomputer** -Aktivität wie folgt.

    |Eigenschaft|Value|
    |--------------|-----------|
    |**Computername**|zuschreiben|
    |**Credential**|Machinecred|
    |**Damit**|Microsoft. PowerShell. Commands. waitforservicetypes. PowerShell|
    |**Force**|True|
    |Warten|True|
    |PSComputerName|{""}|

13. Fügen Sie eine **getwmiobject** -Aktivität der **JoinDomain** -Sequenz nach der **restartcomputer** -Aktivität hinzu. Bearbeiten Sie die zugehörigen Eigenschaften so, dass Sie mit der vorherigen **getwmiobject** -Aktivität identisch sind.

    Wenn Sie die Prozeduren abgeschlossen haben, sollte das Workflow Entwurfs Fenster wie folgt aussehen.

    ![JoinDomain XAML im Workflow-Designer ](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
     ![JoinDomain XAML im Workflow-Designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "Joindomainworkflow")

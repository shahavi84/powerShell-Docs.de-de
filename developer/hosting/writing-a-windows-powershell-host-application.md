---
title: Schreiben eine Windows PowerShell-Hostanwendung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 81aeafad-dbc3-4712-8bb9-e6a417be260f
caps.latest.revision: 15
ms.openlocfilehash: 2df5a59833fcdd58c6b2afbb4882111592fb3d76
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056429"
---
# <a name="writing-a-windows-powershell-host-application"></a><span data-ttu-id="b8af3-102">Schreiben einer Windows PowerShell-Hostanwendung</span><span class="sxs-lookup"><span data-stu-id="b8af3-102">Writing a Windows PowerShell Host Application</span></span>

<span data-ttu-id="b8af3-103">Sie können Windows PowerShell in Ihrer Anwendung hosten.</span><span class="sxs-lookup"><span data-stu-id="b8af3-103">You can host Windows PowerShell in your application.</span></span> <span data-ttu-id="b8af3-104">Die hostanwendung kann den Runspace fest, wo Befehle ausführen, auf einem Computer lokal oder remote-Sitzungen öffnen und rufen Sie die Befehle entweder synchron oder asynchron die Anforderungen der Anwendung abhängig.</span><span class="sxs-lookup"><span data-stu-id="b8af3-104">The host application can define the runspace where commands are run, open sessions on a local or remote computer, and invoke the commands either synchronously or asynchronously based on the needs of the application.</span></span>

<span data-ttu-id="b8af3-105">In den folgenden Themen wird erläutert, wie eine Anwendung, die als Host erstellen</span><span class="sxs-lookup"><span data-stu-id="b8af3-105">The following topics explain how to create an application that hosts</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b8af3-106">In diesem Abschnitt</span><span class="sxs-lookup"><span data-stu-id="b8af3-106">In This Section</span></span>

<span data-ttu-id="b8af3-107">[Windows PowerShell-Host – Schnellstart](./windows-powershell-host-quickstart.md) enthält Anleitungen und Codebeispiele, erhalten Sie Schritte zum Erstellen von hostanwendungen.</span><span class="sxs-lookup"><span data-stu-id="b8af3-107">[Windows PowerShell Host Quickstart](./windows-powershell-host-quickstart.md) Provides instructions and code samples to get you started creating host applications.</span></span>

<span data-ttu-id="b8af3-108">[Erstellen von Runspaces](./creating-runspaces.md) eine Reihe von Themen, die erläutern, wie Sie Runspaces, die zum Ausführen von Windows PowerShell-Befehls in einer hostanwendung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="b8af3-108">[Creating Runspaces](./creating-runspaces.md) A set of topics that explain how to create runspaces to run Windows PowerShell command in a host application.</span></span>

<span data-ttu-id="b8af3-109">[Hinzufügen und Aufrufen von Befehlen](./adding-and-invoking-commands.md) wird erläutert, wie zum Erstellen und Ausführen einer Befehlspipeline in Ihrer hostanwendung...</span><span class="sxs-lookup"><span data-stu-id="b8af3-109">[Adding and invoking commands](./adding-and-invoking-commands.md) Explains how to create and run a command pipeline in your host application..</span></span>

<span data-ttu-id="b8af3-110">[Erstellen remote Runspaces](./creating-remote-runspaces.md) wird erläutert, wie einen Runspace auf einem Remotecomputer herstellen.</span><span class="sxs-lookup"><span data-stu-id="b8af3-110">[Creating remote runspaces](./creating-remote-runspaces.md) Explains how to connect a runspace to a remote computer.</span></span>

<span data-ttu-id="b8af3-111">[Erstellen einer benutzerdefinierten Benutzeroberfläche](./creating-a-custom-user-interface.md) führt benutzerdefinierten Schnittstellen und enthält Links zu Beispielen.</span><span class="sxs-lookup"><span data-stu-id="b8af3-111">[Creating a custom user interface](./creating-a-custom-user-interface.md) Introduces custom user interfaces and provides links to examples.</span></span>

<span data-ttu-id="b8af3-112">[Hosten von Anwendungsbeispielen](./host-application-samples.md) dieser Abschnitt enthält Beispiele für vollständige Hosten von Anwendungen.</span><span class="sxs-lookup"><span data-stu-id="b8af3-112">[Host Application Samples](./host-application-samples.md) This section includes samples of complete host applications.</span></span>

## <a name="see-also"></a><span data-ttu-id="b8af3-113">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b8af3-113">See Also</span></span>

[<span data-ttu-id="b8af3-114">Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b8af3-114">Windows PowerShell</span></span>](http://msdn.microsoft.com/en-us/b41a2af3-aec1-402d-8e18-c2c26be461ff)
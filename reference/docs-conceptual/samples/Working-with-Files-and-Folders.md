---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeiten mit Dateien und Ordnern
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: a8d57a1c269d95e692db6c3f1ae10df49e305e4e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401277"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="ff083-103">Arbeiten mit Dateien und Ordnern</span><span class="sxs-lookup"><span data-stu-id="ff083-103">Working with Files and Folders</span></span>

<span data-ttu-id="ff083-104">Das Navigieren auf Windows PowerShell-Laufwerken und das Bearbeiten der darauf gespeicherten Elemente gleicht dem Bearbeiten von Dateien und Ordnern auf physischen Windows-Festplattenlaufwerken.</span><span class="sxs-lookup"><span data-stu-id="ff083-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="ff083-105">In diesem Abschnitt werden bestimmte Aufgaben im Zusammenhang mit der Bearbeitung von Dateien und Ordnern mithilfe von PowerShell erörtert.</span><span class="sxs-lookup"><span data-stu-id="ff083-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

### <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="ff083-106">Auflisten aller Dateien und Ordner in einem Ordner</span><span class="sxs-lookup"><span data-stu-id="ff083-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="ff083-107">Mit **Get-ChildItem** können Sie alle Elemente abrufen, die sich unmittelbar in einem Ordner befinden.</span><span class="sxs-lookup"><span data-stu-id="ff083-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="ff083-108">Fügen Sie den optionalen Parameter **Force** hinzu, um ausgeblendete oder Systemelemente anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="ff083-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="ff083-109">Dieser Befehl zeigt z. B. den unmittelbaren Inhalt der Windows PowerShell-Laufwerks C: an (dieses entspricht dem physischen Windows-Laufwerk C:):</span><span class="sxs-lookup"><span data-stu-id="ff083-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="ff083-110">Der Befehl listet nur die Elemente auf, die sich unmittelbar in dem Ordner befinden, ähnlich dem „Cmd.exe“-Befehl **DIR** oder **ls** in einer UNIX-Shell.</span><span class="sxs-lookup"><span data-stu-id="ff083-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="ff083-111">Um enthaltene Elemente anzuzeigen, müssen Sie außerdem den Parameter **-Recurse** angeben.</span><span class="sxs-lookup"><span data-stu-id="ff083-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="ff083-112">(Es kann sehr lange dauern, bis dieser Vorgang abgeschlossen ist.) So listen Sie alle Dateien auf Laufwerk C: auf:</span><span class="sxs-lookup"><span data-stu-id="ff083-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="ff083-113">Um mit **Get-ChildItem** Elemente zu filtern, verwenden Sie die Parameter **Path**, **Filter**, **Include** und **Exclude**, die allerdings nur auf Namen basieren.</span><span class="sxs-lookup"><span data-stu-id="ff083-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="ff083-114">Zum Durchführen komplexer Filterung basierend auf anderen Eigenschaften verwenden Sie **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="ff083-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="ff083-115">Der folgende Befehl sucht alle ausführbaren Dateien im Ordner „Programme“, die nach dem 1. Oktober 2005 zuletzt geändert wurden und weder kleiner als 1 MB noch größer als 10 MB sind:</span><span class="sxs-lookup"><span data-stu-id="ff083-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

### <a name="copying-files-and-folders"></a><span data-ttu-id="ff083-116">Kopieren von Dateien und Ordner</span><span class="sxs-lookup"><span data-stu-id="ff083-116">Copying Files and Folders</span></span>

<span data-ttu-id="ff083-117">Das Kopieren erfolgt mit **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="ff083-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="ff083-118">Der folgende Befehl sichert C:\\boot.ini nach C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="ff083-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="ff083-119">Wenn die Zieldatei bereits vorhanden ist, schlägt der Kopierversuch fehl.</span><span class="sxs-lookup"><span data-stu-id="ff083-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="ff083-120">Zum Überschreiben eines vorhandenen Ziels verwenden Sie den Parameter **Force**:</span><span class="sxs-lookup"><span data-stu-id="ff083-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="ff083-121">Dieser Befehl funktioniert auch, wenn das Ziel schreibgeschützt ist.</span><span class="sxs-lookup"><span data-stu-id="ff083-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="ff083-122">Das Kopieren von Ordnern funktioniert auf dieselbe Weise.</span><span class="sxs-lookup"><span data-stu-id="ff083-122">Folder copying works the same way.</span></span> <span data-ttu-id="ff083-123">Dieser Befehl kopiert den Ordner „C:\\temp\\test1“ rekursiv nach „C:\\temp\\DeleteMe“:</span><span class="sxs-lookup"><span data-stu-id="ff083-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="ff083-124">Sie können auch eine Auswahl von Elementen kopieren.</span><span class="sxs-lookup"><span data-stu-id="ff083-124">You can also copy a selection of items.</span></span> <span data-ttu-id="ff083-125">Der folgende Befehl kopiert alle TXT-Dateien, die an beliebiger Stelle in „c:\\data“ enthalten sind, nach „c:\\temp\\text“:</span><span class="sxs-lookup"><span data-stu-id="ff083-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="ff083-126">Sie können auch weiterhin andere Tools verwenden, um Dateisystemkopien auszuführen.</span><span class="sxs-lookup"><span data-stu-id="ff083-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="ff083-127">XCOPY-, ROBOCOPY- und COM-Objekte, z. B. **Scripting.FileSystemObject,** können in Windows PowerShell verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ff083-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="ff083-128">Sie können z.B. die Windows Script Host-Klasse **Scripting.FileSystem COM** verwenden, um „C:\\boot.ini“ nach „C:\\boot.bak“ zu sichern:</span><span class="sxs-lookup"><span data-stu-id="ff083-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

### <a name="creating-files-and-folders"></a><span data-ttu-id="ff083-129">Erstellen von Dateien und Ordnern</span><span class="sxs-lookup"><span data-stu-id="ff083-129">Creating Files and Folders</span></span>

<span data-ttu-id="ff083-130">Das Erstellen neuer Elemente funktioniert auf allen Windows PowerShell-Anbietern gleich.</span><span class="sxs-lookup"><span data-stu-id="ff083-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="ff083-131">Wenn ein Windows PowerShell-Anbieter über mehrere Elementtypen verfügt – der Dateisystem Windows PowerShell-Anbieter z. B. unterscheidet zwischen Verzeichnissen und Dateien – müssen Sie den Elementtyp angeben.</span><span class="sxs-lookup"><span data-stu-id="ff083-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="ff083-132">Dieser Befehl erstellt einen neuen Ordner „C:\\temp\\New Folder“:</span><span class="sxs-lookup"><span data-stu-id="ff083-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="ff083-133">Dieser Befehl erstellt eine neue leere Datei „C:\\temp\\New Folder\\file.txt“.</span><span class="sxs-lookup"><span data-stu-id="ff083-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

### <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="ff083-134">Entfernen aller Dateien und Ordner in einem Ordner</span><span class="sxs-lookup"><span data-stu-id="ff083-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="ff083-135">Mit **Remove-Item** können Sie enthaltene Elemente entfernen. Wenn ein Element weitere Elemente enthält, werden Sie jedoch aufgefordert, das Entfernen zu bestätigen.</span><span class="sxs-lookup"><span data-stu-id="ff083-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="ff083-136">Wenn Sie z.B. versuchen, den Ordner „C:\\temp\\DeleteMe“, der weitere Elemente enthält, zu löschen, fordert Windows PowerShell Sie vor dem Löschen des Ordners zur Bestätigung auf:</span><span class="sxs-lookup"><span data-stu-id="ff083-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ff083-137">Wenn Sie nicht für jedes enthaltene Element aufgefordert werden möchten, geben Sie den Parameter **Recurse** an:</span><span class="sxs-lookup"><span data-stu-id="ff083-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

### <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="ff083-138">Zuordnen eines lokalen Ordners als ein zugreifbares Windows-Laufwerk</span><span class="sxs-lookup"><span data-stu-id="ff083-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="ff083-139">Sie können mithilfe des Befehls **subst** auch einen lokalen Ordner zuordnen.</span><span class="sxs-lookup"><span data-stu-id="ff083-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="ff083-140">Der folgende Befehl erstellt ein lokales geroutetes Laufwerk P: im lokalen Verzeichnis „Programme“:</span><span class="sxs-lookup"><span data-stu-id="ff083-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="ff083-141">Wie bei Netzlaufwerken sind in Windows PowerShell mit **subst** zugeordnete Laufwerke für die Windows PowerShell-Shell sofort sichtbar.</span><span class="sxs-lookup"><span data-stu-id="ff083-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

### <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="ff083-142">Einlesen einer Textdatei in ein Array</span><span class="sxs-lookup"><span data-stu-id="ff083-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="ff083-143">Eine der häufigeren Speicherformate für Textdaten ist eine Datei mit separaten Zeilen, die als einzelne Datenelemente behandelt werden.</span><span class="sxs-lookup"><span data-stu-id="ff083-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="ff083-144">Das Cmdlet **Get-Content** kann zum Lesen einer vollständigen Datei in einem Schritt verwendet werden, wie hier gezeigt:</span><span class="sxs-lookup"><span data-stu-id="ff083-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

<span data-ttu-id="ff083-145">**Get-Content** behandelt die aus der Datei gelesenen Daten bereits als Array, mit je einem Element Dateiinhalt pro Zeile.</span><span class="sxs-lookup"><span data-stu-id="ff083-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="ff083-146">Sie können dies anhand der Länge (**Length**) des zurückgegebenen Inhalts überprüfen:</span><span class="sxs-lookup"><span data-stu-id="ff083-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="ff083-147">Dieser Befehl ist besonders hilfreich zum Abrufen von Listen mit Informationen direkt in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ff083-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="ff083-148">Beispielsweise können Sie eine Liste von Computernamen oder IP-Adressen in einer Datei namens „C:\\temp\\domainMembers.txt“ speichern, wobei in jede Zeile der Datei je ein Name geschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="ff083-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="ff083-149">Mit **Get-Content** können Sie Dateiinhalte abrufen und in die Variable **$Computers** übernehmen:</span><span class="sxs-lookup"><span data-stu-id="ff083-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="ff083-150">**$Computers** ist jetzt ein Array mit einem Computernamen in jedem Element.</span><span class="sxs-lookup"><span data-stu-id="ff083-150">**$Computers** is now an array containing a computer name in each element.</span></span>
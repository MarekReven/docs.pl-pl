---
title: "Przykład technologii podstawowe serializacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ba6670ab5d4580eaf31d5e5c036aedde1bf7d3c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="b400b-102">Przykład technologii podstawowe serializacji</span><span class="sxs-lookup"><span data-stu-id="b400b-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="b400b-103">Pobieranie próbki</span><span class="sxs-lookup"><span data-stu-id="b400b-103">Download sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="b400b-104">W przykładzie pokazano możliwości środowisko uruchomieniowe języka wspólnego firmy do serializacji obiektu wykresu w pamięci w strumieniu.</span><span class="sxs-lookup"><span data-stu-id="b400b-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="b400b-105">W tym przykładzie można użyć dowolnego <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> lub <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> do serializacji.</span><span class="sxs-lookup"><span data-stu-id="b400b-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="b400b-106">Połączonej listy wypełniany danymi, jest serializacji lub deserializacji z strumienia PLiku lub.</span><span class="sxs-lookup"><span data-stu-id="b400b-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="b400b-107">W obu przypadkach zostanie wyświetlona lista, dzięki czemu można wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="b400b-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="b400b-108">Jest typu listy połączonej `LinkedList`, typ zdefiniowany w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b400b-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="b400b-109">Komentarzy w PLikach źródłowych kodu i build.proj uzyskać więcej informacji o serializacji.</span><span class="sxs-lookup"><span data-stu-id="b400b-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="b400b-110">Aby samodzielnie tworzyć przykładowy przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="b400b-110">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="b400b-111">Przejdź do jednego z podkatalogi specyficzne dla języka w katalogu Technologies\Serialization\Runtime Serialization\Basic, za pomocą wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="b400b-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2.  <span data-ttu-id="b400b-112">Typ **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** lub **msbuild SerializationVB.sln**w oparciu o wybór język programowania, w Wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="b400b-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="b400b-113">Aby samodzielnie tworzyć przykładowy przy użyciu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b400b-113">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="b400b-114">Otwórz [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] i przejdź do jednej z przykładowej podkatalogi specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="b400b-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="b400b-115">Kliknij dwukrotnie ikonę PLiku SerializationCS.sln, SerializationJSL.sln lub SerializationVB.sln, w zależności od wybranych przez siebie język programowania, aby otworzyć go w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b400b-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="b400b-116">W **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.</span><span class="sxs-lookup"><span data-stu-id="b400b-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="b400b-117">Przykładowa aplikacja zostanie utworzona w podkatalogu \bin lub \bin\Debug domyślne.</span><span class="sxs-lookup"><span data-stu-id="b400b-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="b400b-118">Aby uruchomić przykładowy</span><span class="sxs-lookup"><span data-stu-id="b400b-118">To run the sample</span></span>  
  
1.  <span data-ttu-id="b400b-119">Przejdź do katalogu zawierającego wbudowanych PLiku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="b400b-119">Navigate to the directory containing the built executable.</span></span>  
  
2.  <span data-ttu-id="b400b-120">Typ **Serialization.exe**, wraz z wartościami parametrów wymaganych, w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="b400b-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b400b-121">Ten przykład tworzy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="b400b-121">This sample builds a console application.</span></span> <span data-ttu-id="b400b-122">Należy uruchomić go za pomocą wiersza polecenia, aby można było wyświetlić dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="b400b-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b400b-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b400b-123">Remarks</span></span>  
 <span data-ttu-id="b400b-124">Przykładowa aplikacja akceptuje wskazujący, który można przetestować parametry wiersza polecenia chcesz wykonać.</span><span class="sxs-lookup"><span data-stu-id="b400b-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="b400b-125">Do serializacji listę 10 węzła w pliku o nazwie **Test.xml** przy użyciu elementu formatującego SOAP, użyj parametrów **sx Test.xml 10**.</span><span class="sxs-lookup"><span data-stu-id="b400b-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="b400b-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b400b-126">For Example:</span></span>  
  
 <span data-ttu-id="b400b-127">**Serialize.exe - sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="b400b-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="b400b-128">Do deserializacji **Test.xml** pliku z poprzedniego przykładu, użyj parametrów **dx Test.xml**.</span><span class="sxs-lookup"><span data-stu-id="b400b-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="b400b-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b400b-129">For Example:</span></span>  
  
 <span data-ttu-id="b400b-130">**Test.xml - dx Serialize.exe**</span><span class="sxs-lookup"><span data-stu-id="b400b-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="b400b-131">W dwóch przykładach "x" przełącznika wiersza polecenia oznacza, że chcesz serializacji XML protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b400b-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="b400b-132">"B" można użyć w tym miejscu można użyć serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="b400b-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="b400b-133">Jeśli chcesz spróbować serializacji z bardzo dużej liczby węzłów, można przekierować dane wyjściowe z konsoli do PLiku.</span><span class="sxs-lookup"><span data-stu-id="b400b-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="b400b-134">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="b400b-134">For Example:</span></span>  
  
 <span data-ttu-id="b400b-135">**Serialize.exe - sb Test.bin 10000 > somefile.txt**</span><span class="sxs-lookup"><span data-stu-id="b400b-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="b400b-136">Następujące punktory krótko opisano klasy i technologie używane w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b400b-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
-   <span data-ttu-id="b400b-137">Środowisko wykonawcze serializacji</span><span class="sxs-lookup"><span data-stu-id="b400b-137">Runtime Serialization</span></span>  
  
    -   <span data-ttu-id="b400b-138"><xref:System.Runtime.Serialization.IFormatter>Odnosi się do albo <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> lub <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="b400b-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    -   <span data-ttu-id="b400b-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>Służy do serializacji połączonej listy w strumieniu w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="b400b-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="b400b-140">Binarny program formatujący używa formatu tylko <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> rozumie typu.</span><span class="sxs-lookup"><span data-stu-id="b400b-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="b400b-141">Jednak dane są zwięzły.</span><span class="sxs-lookup"><span data-stu-id="b400b-141">However, the data is concise.</span></span>  
  
    -   <span data-ttu-id="b400b-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>Służy do serializacji połączonej listy w strumieniu w formacie protokołu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b400b-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="b400b-143">Protokołu SOAP jest to standardowy format.</span><span class="sxs-lookup"><span data-stu-id="b400b-143">SOAP is a standard format.</span></span>  
  
-   <span data-ttu-id="b400b-144">We/Wy strumienia</span><span class="sxs-lookup"><span data-stu-id="b400b-144">Stream I/O</span></span>  
  
    -   <span data-ttu-id="b400b-145"><xref:System.IO.Stream>Służy do serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="b400b-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="b400b-146">Typ określonego strumienia używane w tym przykładzie jest <xref:System.IO.FileStream> typu.</span><span class="sxs-lookup"><span data-stu-id="b400b-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="b400b-147">Jednak można użyć serializacji z dowolnego typu opracowane na podstawie <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="b400b-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    -   <span data-ttu-id="b400b-148"><xref:System.IO.File>Służy do tworzenia <xref:System.IO.FileStream> obiektów do odczytywania i tworzenia PLików na dysku.</span><span class="sxs-lookup"><span data-stu-id="b400b-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    -   <span data-ttu-id="b400b-149"><xref:System.IO.FileStream>Służy do serializacji i deserializacji połączonej listy.</span><span class="sxs-lookup"><span data-stu-id="b400b-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b400b-150">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b400b-150">See Also</span></span>  
 <xref:System.IO>  
 <xref:System.IO.File>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.Stream>  
 <xref:System.Random>  
 <xref:System.Runtime.Serialization>  
 <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
 <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>  
 <xref:System.Runtime.Serialization.IFormatter>  
 <xref:System.SerializableAttribute>  
 <xref:System.Xml.Serialization>  
 [<span data-ttu-id="b400b-151">Podstawowe serializacji</span><span class="sxs-lookup"><span data-stu-id="b400b-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="b400b-152">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="b400b-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="b400b-153">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="b400b-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="b400b-154">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="b400b-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="b400b-155">Serializacja</span><span class="sxs-lookup"><span data-stu-id="b400b-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="b400b-156">XML i serializacji SOAP</span><span class="sxs-lookup"><span data-stu-id="b400b-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
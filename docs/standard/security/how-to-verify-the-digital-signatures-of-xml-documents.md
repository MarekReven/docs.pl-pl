---
title: "Porady: sprawdzanie podpisów cyfrowych w dokumentach XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- System.Security.Cryptography.SignedXml class
- signatures, cryptographic
- System.Security.Cryptography.RSACryptoServiceProvider class
- verifying signatures
- checking signatures
- XML digital signatures
- digital signatures, verifying
ms.assetid: a4d5ceb1-b9f5-47e8-9e4a-a2b39110002f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a2c8cf23e1f00d6deac52f3c4bee8932b7c487a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-verify-the-digital-signatures-of-xml-documents"></a><span data-ttu-id="c8380-102">Porady: sprawdzanie podpisów cyfrowych w dokumentach XML</span><span class="sxs-lookup"><span data-stu-id="c8380-102">How to: Verify the Digital Signatures of XML Documents</span></span>
<span data-ttu-id="c8380-103">Można użyć klasy w <xref:System.Security.Cryptography.Xml> przestrzeni nazw, aby sprawdzić, dane XML podpisane za pomocą podpisu cyfrowego.</span><span class="sxs-lookup"><span data-stu-id="c8380-103">You can use the classes in the <xref:System.Security.Cryptography.Xml> namespace to verify XML data signed with a digital signature.</span></span>  <span data-ttu-id="c8380-104">Podpisy cyfrowe XML (XMLDSIG) pozwalają sprawdzić, czy dane nie została zmodyfikowana po podpisaniu.</span><span class="sxs-lookup"><span data-stu-id="c8380-104">XML digital signatures (XMLDSIG) allow you to verify that data was not altered after it was signed.</span></span>  <span data-ttu-id="c8380-105">Aby uzyskać więcej informacji na temat XMLDSIG standardowe zobacz specyfikację sieci World Wide Web konsorcjum W3C w http://www.w3.org/TR/xmldsig-core/.</span><span class="sxs-lookup"><span data-stu-id="c8380-105">For more information about the XMLDSIG standard, see the World Wide Web Consortium (W3C) specification at http://www.w3.org/TR/xmldsig-core/.</span></span>  
  
 <span data-ttu-id="c8380-106">Przykład kodu w tej procedurze pokazano, jak można zweryfikować podpisu cyfrowego XML zawarte w <`Signature`> elementu.</span><span class="sxs-lookup"><span data-stu-id="c8380-106">The code example in this procedure demonstrates how to verify an XML digital signature contained in a <`Signature`> element.</span></span>  <span data-ttu-id="c8380-107">Przykład pobiera klucza publicznego RSA z kontenera kluczy, a następnie używa klucza można zweryfikować podpisu.</span><span class="sxs-lookup"><span data-stu-id="c8380-107">The example retrieves an RSA public key from a key container and then uses the key to verify the signature.</span></span>  
  
 <span data-ttu-id="c8380-108">Aby uzyskać informacje o tym, jak utworzyć podpis cyfrowy, który można sprawdzić za pomocą tej metody, zobacz [porady: znak dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="c8380-108">For information about how create a digital signature that can be verified using this technique, see [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
### <a name="to-verify-the-digital-signature-of-an-xml-document"></a><span data-ttu-id="c8380-109">Aby sprawdzić podpis cyfrowy dokumentu XML</span><span class="sxs-lookup"><span data-stu-id="c8380-109">To verify the digital signature of an XML document</span></span>  
  
1.  <span data-ttu-id="c8380-110">Aby sprawdzić dokumentu, należy użyć tego samego klucza asymetrycznego, który został użyty do podpisywania.</span><span class="sxs-lookup"><span data-stu-id="c8380-110">To verify the document, you must use the same asymmetric key that was used for signing.</span></span>  <span data-ttu-id="c8380-111">Utwórz <xref:System.Security.Cryptography.CspParameters> obiektu i określ nazwę kontenera klucza, który został użyty do podpisywania.</span><span class="sxs-lookup"><span data-stu-id="c8380-111">Create a <xref:System.Security.Cryptography.CspParameters> object and specify the name of the key container that was used for signing.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#2)]
     [!code-vb[HowToVerifyXMLDocumentRSA#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#2)]  
  
2.  <span data-ttu-id="c8380-112">Pobrać publicznego klucza za pomocą <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="c8380-112">Retrieve the public key using the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  <span data-ttu-id="c8380-113">Klucz jest ładowane automatycznie przy użyciu kontenera kluczy według nazwy podczas przekazywania <xref:System.Security.Cryptography.CspParameters> obiekt do konstruktora obiektu <xref:System.Security.Cryptography.RSACryptoServiceProvider> klasy.</span><span class="sxs-lookup"><span data-stu-id="c8380-113">The key is automatically loaded from the key container by name when you pass the <xref:System.Security.Cryptography.CspParameters> object to the constructor of the <xref:System.Security.Cryptography.RSACryptoServiceProvider> class.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#3)]
     [!code-vb[HowToVerifyXMLDocumentRSA#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#3)]  
  
3.  <span data-ttu-id="c8380-114">Utwórz <xref:System.Xml.XmlDocument> obiektu przez ładowanie pliku XML z dysku.</span><span class="sxs-lookup"><span data-stu-id="c8380-114">Create an <xref:System.Xml.XmlDocument> object by loading an XML file from disk.</span></span>  <span data-ttu-id="c8380-115"><xref:System.Xml.XmlDocument> Obiekt zawiera podpisanego dokumentu XML można zweryfikować.</span><span class="sxs-lookup"><span data-stu-id="c8380-115">The <xref:System.Xml.XmlDocument> object contains the signed XML document to verify.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#4)]
     [!code-vb[HowToVerifyXMLDocumentRSA#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#4)]  
  
4.  <span data-ttu-id="c8380-116">Utwórz nową <xref:System.Security.Cryptography.Xml.SignedXml> obiektu i przekazać <xref:System.Xml.XmlDocument> obiektu do niego.</span><span class="sxs-lookup"><span data-stu-id="c8380-116">Create a new <xref:System.Security.Cryptography.Xml.SignedXml> object and pass the <xref:System.Xml.XmlDocument> object to it.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#5)]
     [!code-vb[HowToVerifyXMLDocumentRSA#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#5)]  
  
5.  <span data-ttu-id="c8380-117">Znajdź <`signature`> element i utworzyć nową <xref:System.Xml.XmlNodeList> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c8380-117">Find the <`signature`> element and create a new <xref:System.Xml.XmlNodeList> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#6)]
     [!code-vb[HowToVerifyXMLDocumentRSA#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#6)]  
  
6.  <span data-ttu-id="c8380-118">Ładowanie pliku XML pierwszego <`signature`> element do <xref:System.Security.Cryptography.Xml.SignedXml> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c8380-118">Load the XML of the first <`signature`> element into the <xref:System.Security.Cryptography.Xml.SignedXml> object.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#7)]
     [!code-vb[HowToVerifyXMLDocumentRSA#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#7)]  
  
7.  <span data-ttu-id="c8380-119">Sprawdzanie podpisu przy użyciu <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> — metoda i klucza publicznego RSA.</span><span class="sxs-lookup"><span data-stu-id="c8380-119">Check the signature using the <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignature%2A> method and the RSA public key.</span></span>  <span data-ttu-id="c8380-120">Ta metoda zwraca wartość logiczną, która wskazuje powodzenie lub niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="c8380-120">This method returns a Boolean value that indicates success or failure.</span></span>  
  
     [!code-csharp[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#8)]
     [!code-vb[HowToVerifyXMLDocumentRSA#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#8)]  
  
## <a name="example"></a><span data-ttu-id="c8380-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="c8380-121">Example</span></span>  
 <span data-ttu-id="c8380-122">W tym przykładzie przyjęto założenie, że plik o nazwie `"test.xml"` istnieje w tym samym katalogu co program skompilowany.</span><span class="sxs-lookup"><span data-stu-id="c8380-122">This example assumes that a file named `"test.xml"` exists in the same directory as the compiled program.</span></span>  <span data-ttu-id="c8380-123">`"test.xml"` Pliku muszą być podpisane za pomocą metod opisanych w [porady: znak dokumentów XML za pomocą podpisów cyfrowych](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span><span class="sxs-lookup"><span data-stu-id="c8380-123">The `"test.xml"` file must be signed using the techniques described in [How to: Sign XML Documents with Digital Signatures](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md).</span></span>  
  
 [!code-csharp[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/cs/sample.cs#1)]
 [!code-vb[HowToVerifyXMLDocumentRSA#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToVerifyXMLDocumentRSA/vb/sample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8380-124">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c8380-124">Compiling the Code</span></span>  
  
-   <span data-ttu-id="c8380-125">Aby skompilować w tym przykładzie, należy uwzględnić odwołania do `System.Security.dll`.</span><span class="sxs-lookup"><span data-stu-id="c8380-125">To compile this example, you need to include a reference to `System.Security.dll`.</span></span>  
  
-   <span data-ttu-id="c8380-126">Obejmują następujących przestrzeni nazw: <xref:System.Xml>, <xref:System.Security.Cryptography>, i <xref:System.Security.Cryptography.Xml>.</span><span class="sxs-lookup"><span data-stu-id="c8380-126">Include the following namespaces: <xref:System.Xml>, <xref:System.Security.Cryptography>, and <xref:System.Security.Cryptography.Xml>.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c8380-127">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="c8380-127">.NET Framework Security</span></span>  
 <span data-ttu-id="c8380-128">Nigdy nie magazynu lub przenieść klucz prywatny para kluczy asymetrycznych w postaci zwykłego tekstu.</span><span class="sxs-lookup"><span data-stu-id="c8380-128">Never store or transfer the private key of an asymmetric key pair in plaintext.</span></span>  <span data-ttu-id="c8380-129">Aby uzyskać więcej informacji na temat symetrycznego i asymetrycznego kluczy kryptograficznych, zobacz [Generowanie kluczy szyfrowania i odszyfrowywania](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span><span class="sxs-lookup"><span data-stu-id="c8380-129">For more information about symmetric and asymmetric cryptographic keys, see [Generating Keys for Encryption and Decryption](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md).</span></span>  
  
 <span data-ttu-id="c8380-130">Nigdy nie osadzaj klucza prywatnego bezpośrednio w kodzie źródłowym.</span><span class="sxs-lookup"><span data-stu-id="c8380-130">Never embed a private key directly into your source code.</span></span>  <span data-ttu-id="c8380-131">Osadzony kluczy można łatwo odczytać z zestawu za pomocą [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) lub przez otwarcie zestawu w edytorze tekstu, takiego jak Notatnik.</span><span class="sxs-lookup"><span data-stu-id="c8380-131">Embedded keys can be easily read from an assembly using the [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by opening the assembly in a text editor such as Notepad.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8380-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8380-132">See Also</span></span>  
 <xref:System.Security.Cryptography.Xml>  
 [<span data-ttu-id="c8380-133">Porady: podpisywanie dokumentów XML za pomocą podpisów cyfrowych</span><span class="sxs-lookup"><span data-stu-id="c8380-133">How to: Sign XML Documents with Digital Signatures</span></span>](../../../docs/standard/security/how-to-sign-xml-documents-with-digital-signatures.md)
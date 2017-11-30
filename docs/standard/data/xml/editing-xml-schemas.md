---
title: Edytowanie schematy XML
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
- cpp
ms.assetid: fa09c8e5-c2b9-49d2-bb0d-40330cd13e4d
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9505f60b2000ef227463404dab051ecb7fa3cc5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="editing-xml-schemas"></a><span data-ttu-id="6b783-102">Edytowanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="6b783-102">Editing XML Schemas</span></span>
<span data-ttu-id="6b783-103">Edytowanie schematu XML jest jednym z najważniejszych elementów z modelu obiektu schematu (SOM).</span><span class="sxs-lookup"><span data-stu-id="6b783-103">Editing an XML schema is one of the most important features of the Schema Object Model (SOM).</span></span> <span data-ttu-id="6b783-104">Wszystkie właściwości wstępnie przygotowany schema kompilacji SOM można zmienić istniejące wartości w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="6b783-104">All of the pre-schema-compilation properties of the SOM can be used to change the existing values in an XML schema.</span></span> <span data-ttu-id="6b783-105">Schemat XML można następnie ponownie skompilowana, aby odzwierciedlić zmiany.</span><span class="sxs-lookup"><span data-stu-id="6b783-105">The XML schema can then be recompiled to reflect the changes.</span></span>  
  
 <span data-ttu-id="6b783-106">Pierwszym krokiem w schemacie ładowane do SOM edycji jest przechodzenia schematu.</span><span class="sxs-lookup"><span data-stu-id="6b783-106">The first step in editing a schema loaded into the SOM is to traverse the schema.</span></span> <span data-ttu-id="6b783-107">Należy zapoznać się z przechodzących przez schemat przy użyciu interfejsu API SOM, przed przystąpieniem do edytowania schematu.</span><span class="sxs-lookup"><span data-stu-id="6b783-107">You should be familiar with traversing a schema using the SOM API before you attempt to edit a schema.</span></span> <span data-ttu-id="6b783-108">Należy także zapoznać się z właściwości przed i po schema kompilacji po-schema-kompilacji-typu Infoset (PSCI).</span><span class="sxs-lookup"><span data-stu-id="6b783-108">You should also be familiar with the pre- and post-schema-compilation properties of the Post-Schema-Compilation-Infoset (PSCI).</span></span>  
  
## <a name="editing-an-xml-schema"></a><span data-ttu-id="6b783-109">Edytowanie schematu XML</span><span class="sxs-lookup"><span data-stu-id="6b783-109">Editing an XML Schema</span></span>  
 <span data-ttu-id="6b783-110">W tej sekcji podano dwa przykłady kodu, które Edytowanie schematu klienta utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="6b783-110">In this section, two code examples are provided, both of which edit the customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span> <span data-ttu-id="6b783-111">W pierwszym przykładzie kodu dodaje nowy `PhoneNumber` elementu `Customer` dodaje nowy element, a w drugim przykładzie kodu `Title` atrybutu `FirstName` elementu.</span><span class="sxs-lookup"><span data-stu-id="6b783-111">The first code example adds a new `PhoneNumber` element to the `Customer` element and the second code example adds a new `Title` attribute to the `FirstName` element.</span></span> <span data-ttu-id="6b783-112">Pierwszym przykładzie użyto również po-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji jako środek przechodzących przez schemat klienta podczas drugi przykład kodu wykorzystuje wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b783-112">The first sample also uses the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection as the means of traversing the customer schema while the second code example uses the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
### <a name="phonenumber-element-example"></a><span data-ttu-id="6b783-113">Przykład elementu numer telefonu</span><span class="sxs-lookup"><span data-stu-id="6b783-113">PhoneNumber Element Example</span></span>  
 <span data-ttu-id="6b783-114">W tym przykładzie pierwsze kodu dodaje nowy `PhoneNumber` elementu `Customer` elementu schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="6b783-114">This first code example adds a new `PhoneNumber` element to the `Customer` element of the customer schema.</span></span> <span data-ttu-id="6b783-115">Przykładowy kod edytuje schematu klienta w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="6b783-115">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="6b783-116">Dodaje do nowego schematu klienta <xref:System.Xml.Schema.XmlSchemaSet> obiekt, a następnie kompiluje go.</span><span class="sxs-lookup"><span data-stu-id="6b783-116">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="6b783-117">Wszelkie ostrzeżenia dotyczące sprawdzania poprawności schematu i błędów napotkanych odczytu lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="6b783-117">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="6b783-118">Pobiera skompilowanych <xref:System.Xml.Schema.XmlSchema> obiekt z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie po <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b783-118">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="6b783-119">Ponieważ skompilować schematu, po-Schema-kompilacji-typu Infoset właściwości (PSCI) są dostępne.</span><span class="sxs-lookup"><span data-stu-id="6b783-119">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="6b783-120">Tworzy `PhoneNumber` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaElement> klasy `xs:string` za pomocą ograniczenia typu prostego <xref:System.Xml.Schema.XmlSchemaSimpleType> i <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> klas, dodaje zestaw reguł wzorca do <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> właściwości ograniczenia i dodaje ograniczenia <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> właściwość typu prostego i typu prostego do <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> z `PhoneNumber` elementu.</span><span class="sxs-lookup"><span data-stu-id="6b783-120">Creates the `PhoneNumber` element using the <xref:System.Xml.Schema.XmlSchemaElement> class, the `xs:string` simple type restriction using the <xref:System.Xml.Schema.XmlSchemaSimpleType> and <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction> classes, adds a pattern facet to the <xref:System.Xml.Schema.XmlSchemaSimpleTypeRestriction.Facets%2A> property of the restriction, and adds the restriction to the <xref:System.Xml.Schema.XmlSchemaSimpleType.Content%2A> property of the simple type and the simple type to the <xref:System.Xml.Schema.XmlSchemaElement.SchemaType%2A> of the `PhoneNumber` element.</span></span>  
  
4.  <span data-ttu-id="6b783-121">Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaElement> w <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> kolekcji po-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b783-121">Iterates over each <xref:System.Xml.Schema.XmlSchemaElement> in the <xref:System.Xml.Schema.XmlSchemaObjectTable.Values%2A> collection of the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span>  
  
5.  <span data-ttu-id="6b783-122">Jeśli <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> elementu jest `"Customer"`, pobiera typ złożony `Customer` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstka sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.</span><span class="sxs-lookup"><span data-stu-id="6b783-122">If the <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> of the element is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
6.  <span data-ttu-id="6b783-123">Dodaje nowy `PhoneNumber` element zawierający istniejącej sekwencji `FirstName` i `LastName` elementów za pomocą wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> kolekcji sekwencji.</span><span class="sxs-lookup"><span data-stu-id="6b783-123">Adds the new `PhoneNumber` element to the sequence containing the existing `FirstName` and `LastName` elements using the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A> collection of the sequence.</span></span>  
  
7.  <span data-ttu-id="6b783-124">Na koniec ponownego przetwarzania i kompiluje zmodyfikowanych <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.</span><span class="sxs-lookup"><span data-stu-id="6b783-124">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="6b783-125">Poniżej znajduje się pełny przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="6b783-125">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample1#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample1/CPP/XmlSchemaEditExample1.cpp#1)]
 [!code-csharp[XmlSchemaEditExample1#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample1/CS/XmlSchemaEditExample1.cs#1)]
 [!code-vb[XmlSchemaEditExample1#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample1/VB/XmlSchemaEditExample1.vb#1)]  
  
 <span data-ttu-id="6b783-126">Poniżej przedstawiono schematu klienta zmodyfikowane utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="6b783-126">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="xs:string" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
        <xs:element name="PhoneNumber">           <xs:simpleType>             <xs:restriction base="xs:string">               <xs:pattern value="\d{3}-\d{3}-\d(4)" />             </xs:restriction>           </xs:simpleType>         </xs:element>  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
### <a name="title-attribute-example"></a><span data-ttu-id="6b783-127">Przykład atrybutu tytułu</span><span class="sxs-lookup"><span data-stu-id="6b783-127">Title Attribute Example</span></span>  
 <span data-ttu-id="6b783-128">W tym drugim przykładzie kodu dodaje nowy `Title` atrybutu `FirstName` elementu schematu klienta.</span><span class="sxs-lookup"><span data-stu-id="6b783-128">This second code example, adds a new `Title` attribute to the `FirstName` element of the customer schema.</span></span> <span data-ttu-id="6b783-129">W pierwszym przykładzie kodu typu `FirstName` jest element `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="6b783-129">In the first code example, the type of the `FirstName` element is `xs:string`.</span></span> <span data-ttu-id="6b783-130">Aby uzyskać `FirstName` element ma atrybut wraz z ciągu zawartości, należy zmienić jego typ do typu złożone o prostym rozszerzeniu zawartości modelu zawartości.</span><span class="sxs-lookup"><span data-stu-id="6b783-130">For the `FirstName` element to have an attribute along with string content, its type must be changed to a complex type with a simple content extension content model.</span></span>  
  
 <span data-ttu-id="6b783-131">Przykładowy kod edytuje schematu klienta w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="6b783-131">The code example edits the customer schema in the following steps.</span></span>  
  
1.  <span data-ttu-id="6b783-132">Dodaje do nowego schematu klienta <xref:System.Xml.Schema.XmlSchemaSet> obiekt, a następnie kompiluje go.</span><span class="sxs-lookup"><span data-stu-id="6b783-132">Adds the customer schema to a new <xref:System.Xml.Schema.XmlSchemaSet> object and then compiles it.</span></span> <span data-ttu-id="6b783-133">Wszelkie ostrzeżenia dotyczące sprawdzania poprawności schematu i błędów napotkanych odczytu lub kompilowania schematu są obsługiwane przez <xref:System.Xml.Schema.ValidationEventHandler> delegowanie.</span><span class="sxs-lookup"><span data-stu-id="6b783-133">Any schema validation warnings and errors encountered reading or compiling the schema are handled by the <xref:System.Xml.Schema.ValidationEventHandler> delegate.</span></span>  
  
2.  <span data-ttu-id="6b783-134">Pobiera skompilowanych <xref:System.Xml.Schema.XmlSchema> obiekt z <xref:System.Xml.Schema.XmlSchemaSet> przez Iterowanie po <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="6b783-134">Retrieves the compiled <xref:System.Xml.Schema.XmlSchema> object from the <xref:System.Xml.Schema.XmlSchemaSet> by iterating over the <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> property.</span></span> <span data-ttu-id="6b783-135">Ponieważ skompilować schematu, po-Schema-kompilacji-typu Infoset właściwości (PSCI) są dostępne.</span><span class="sxs-lookup"><span data-stu-id="6b783-135">Because the schema is compiled, Post-Schema-Compilation-Infoset (PSCI) properties are accessible.</span></span>  
  
3.  <span data-ttu-id="6b783-136">Tworzy nowy typ złożony dla `FirstName` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy.</span><span class="sxs-lookup"><span data-stu-id="6b783-136">Creates a new complex type for the `FirstName` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class.</span></span>  
  
4.  <span data-ttu-id="6b783-137">Tworzy nowy prostym rozszerzeniu zawartości, z podstawowym typem `xs:string`za pomocą <xref:System.Xml.Schema.XmlSchemaSimpleContent> i <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="6b783-137">Creates a new simple content extension, with a base type of `xs:string`, using the <xref:System.Xml.Schema.XmlSchemaSimpleContent> and <xref:System.Xml.Schema.XmlSchemaSimpleContentExtension> classes.</span></span>  
  
5.  <span data-ttu-id="6b783-138">Tworzy nowy `Title` atrybutu przy użyciu <xref:System.Xml.Schema.XmlSchemaAttribute> klasy, z <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> z `xs:string` i dodaje atrybut do prostym rozszerzeniu zawartości.</span><span class="sxs-lookup"><span data-stu-id="6b783-138">Creates the new `Title` attribute using the <xref:System.Xml.Schema.XmlSchemaAttribute> class, with a <xref:System.Xml.Schema.XmlSchemaAttribute.SchemaTypeName%2A> of `xs:string` and adds the attribute to the simple content extension.</span></span>  
  
6.  <span data-ttu-id="6b783-139">Ustawia model zawartości prostej zawartości prostym rozszerzeniu zawartości i model zawartości typu złożonego do prostej zawartości.</span><span class="sxs-lookup"><span data-stu-id="6b783-139">Sets the content model of the simple content to the simple content extension and the content model of the complex type to the simple content.</span></span>  
  
7.  <span data-ttu-id="6b783-140">Dodaje nowy typ złożony do wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b783-140">Adds the new complex type to the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
8.  <span data-ttu-id="6b783-141">Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaObject> w próbnej-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b783-141">Iterates over each <xref:System.Xml.Schema.XmlSchemaObject> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b783-142">Ponieważ `FirstName` element nie jest element globalny w schemacie, nie jest dostępna w <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> lub <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b783-142">Because the `FirstName` element is not a global element in the schema, it is not available in the <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> or <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collections.</span></span> <span data-ttu-id="6b783-143">Przykładowy kod lokalizuje `FirstName` element dzięki umieszczeniu pierwszy `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="6b783-143">The code example locates the `FirstName` element by first locating the `Customer` element.</span></span>  
>   
>  <span data-ttu-id="6b783-144">W pierwszym przykładzie kodu przechodzić schematu za pomocą po-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b783-144">The first code example traversed the schema using the post-schema-compilation <xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="6b783-145">W tym przykładzie, wstępnie przygotowany-schema-kompilacji <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> kolekcja jest używana do przechodzenia schematu.</span><span class="sxs-lookup"><span data-stu-id="6b783-145">In this sample, the pre-schema-compilation <xref:System.Xml.Schema.XmlSchema.Items%2A?displayProperty=nameWithType> collection is used to traverse the schema.</span></span> <span data-ttu-id="6b783-146">Gdy obie kolekcje zapewniają dostęp do globalnego elementy w schemacie, iteracji <xref:System.Xml.Schema.XmlSchema.Items%2A> kolekcji jest bardziej czasochłonne, ponieważ musi przejść przez wszystkie elementy globalny w schemacie i nie ma żadnych właściwości PSCI.</span><span class="sxs-lookup"><span data-stu-id="6b783-146">While both collections provide access to the global elements in the schema, iterating through the <xref:System.Xml.Schema.XmlSchema.Items%2A> collection is more time consuming because you must iterate over all global elements in the schema and it does not have any PSCI properties.</span></span> <span data-ttu-id="6b783-147">Kolekcje PSCI (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>i tak dalej) zapewniać bezpośredni dostęp do ich globalne elementy, atrybuty i typy oraz ich właściwości PSCI.</span><span class="sxs-lookup"><span data-stu-id="6b783-147">The PSCI collections (<xref:System.Xml.Schema.XmlSchema.Elements%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.Attributes%2A?displayProperty=nameWithType>, <xref:System.Xml.Schema.XmlSchema.SchemaTypes%2A?displayProperty=nameWithType>, and so on) provide direct access to their global elements, attributes, and types and their PSCI properties.</span></span>  
  
1.  <span data-ttu-id="6b783-148">Jeśli <xref:System.Xml.Schema.XmlSchemaObject> to element, którego <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"Customer"`, pobiera typ złożony `Customer` przy użyciu elementu <xref:System.Xml.Schema.XmlSchemaComplexType> klasy i cząstka sequence użycia typu złożonego <xref:System.Xml.Schema.XmlSchemaSequence> klasy.</span><span class="sxs-lookup"><span data-stu-id="6b783-148">If the <xref:System.Xml.Schema.XmlSchemaObject> is an element, whose <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"Customer"`, gets the complex type of the `Customer` element using the <xref:System.Xml.Schema.XmlSchemaComplexType> class and the sequence particle of the complex type using the <xref:System.Xml.Schema.XmlSchemaSequence> class.</span></span>  
  
2.  <span data-ttu-id="6b783-149">Wykonuje iterację na każdym <xref:System.Xml.Schema.XmlSchemaParticle> w próbnej-schema-kompilacji <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="6b783-149">Iterates over each <xref:System.Xml.Schema.XmlSchemaParticle> in the pre-schema-compilation <xref:System.Xml.Schema.XmlSchemaSequence.Items%2A?displayProperty=nameWithType> collection.</span></span>  
  
3.  <span data-ttu-id="6b783-150">Jeśli <xref:System.Xml.Schema.XmlSchemaParticle> jest elementem, który w <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> jest `"FirstName"`, ustawia <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> z `FirstName` element do nowego `FirstName` typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="6b783-150">If the <xref:System.Xml.Schema.XmlSchemaParticle> is an element, who's <xref:System.Xml.Schema.XmlSchemaElement.QualifiedName%2A> is `"FirstName"`, sets the <xref:System.Xml.Schema.XmlSchemaElement.SchemaTypeName%2A> of the `FirstName` element to the new `FirstName` complex type.</span></span>  
  
4.  <span data-ttu-id="6b783-151">Na koniec ponownego przetwarzania i kompiluje zmodyfikowanych <xref:System.Xml.Schema.XmlSchema> przy użyciu <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> i <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody <xref:System.Xml.Schema.XmlSchemaSet> klasy i zapisuje go w konsoli.</span><span class="sxs-lookup"><span data-stu-id="6b783-151">Finally, reprocesses and compiles the modified <xref:System.Xml.Schema.XmlSchema> object using the <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> and <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> methods of the <xref:System.Xml.Schema.XmlSchemaSet> class and writes it to the console.</span></span>  
  
 <span data-ttu-id="6b783-152">Poniżej znajduje się pełny przykład kodu.</span><span class="sxs-lookup"><span data-stu-id="6b783-152">The following is the complete code example.</span></span>  
  
 [!code-cpp[XmlSchemaEditExample2#1](../../../../samples/snippets/cpp/VS_Snippets_Data/XmlSchemaEditExample2/CPP/XmlSchemaEditExample2.cpp#1)]
 [!code-csharp[XmlSchemaEditExample2#1](../../../../samples/snippets/csharp/VS_Snippets_Data/XmlSchemaEditExample2/CS/XmlSchemaEditExample2.cs#1)]
 [!code-vb[XmlSchemaEditExample2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XmlSchemaEditExample2/VB/XmlSchemaEditExample2.vb#1)]  
  
 <span data-ttu-id="6b783-153">Poniżej przedstawiono schematu klienta zmodyfikowane utworzone w [schematów XML budynku](../../../../docs/standard/data/xml/building-xml-schemas.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="6b783-153">The following is the modified customer schema created in the [Building XML Schemas](../../../../docs/standard/data/xml/building-xml-schemas.md) topic.</span></span>  
  
```xml  
<?xml version="1.0" encoding=" utf-8"?>  
<xs:schema xmlns:tns="http://www.tempuri.org" targetNamespace="http://www.tempuri.org" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  <xs:element name="Customer">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="FirstName" type="tns:FirstNameComplexType" />  
        <xs:element name="LastName" type="tns:LastNameType" />  
      </xs:sequence>  
      <xs:attribute name="CustomerId" type="xs:positiveInteger" use="required" /  
>  
    </xs:complexType>  
  </xs:element>  
  <xs:simpleType name="LastNameType">  
    <xs:restriction base="xs:string">  
      <xs:maxLength value="20" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:complexType name="FirstNameComplexType">     <xs:simpleContent>       <xs:extension base="xs:string">         <xs:attribute name="Title" type="xs:string" />       </xs:extension>     </xs:simpleContent>   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b783-154">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b783-154">See Also</span></span>  
 [<span data-ttu-id="6b783-155">Omówienie modelu obiektu schematu XML</span><span class="sxs-lookup"><span data-stu-id="6b783-155">XML Schema Object Model Overview</span></span>](../../../../docs/standard/data/xml/xml-schema-object-model-overview.md)  
 [<span data-ttu-id="6b783-156">Odczytywanie i zapisywanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="6b783-156">Reading and Writing XML Schemas</span></span>](../../../../docs/standard/data/xml/reading-and-writing-xml-schemas.md)  
 [<span data-ttu-id="6b783-157">Tworzenie schematów XML</span><span class="sxs-lookup"><span data-stu-id="6b783-157">Building XML Schemas</span></span>](../../../../docs/standard/data/xml/building-xml-schemas.md)  
 [<span data-ttu-id="6b783-158">Przechodzenie przez schematy XML</span><span class="sxs-lookup"><span data-stu-id="6b783-158">Traversing XML Schemas</span></span>](../../../../docs/standard/data/xml/traversing-xml-schemas.md)  
 [<span data-ttu-id="6b783-159">W tym lub importowanie schematy XML</span><span class="sxs-lookup"><span data-stu-id="6b783-159">Including or Importing XML Schemas</span></span>](../../../../docs/standard/data/xml/including-or-importing-xml-schemas.md)  
 [<span data-ttu-id="6b783-160">Zestaw XmlSchemaSet schematu kompilacji</span><span class="sxs-lookup"><span data-stu-id="6b783-160">XmlSchemaSet for Schema Compilation</span></span>](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [<span data-ttu-id="6b783-161">Obiekt typu Infoset schematu po kompilacji</span><span class="sxs-lookup"><span data-stu-id="6b783-161">Post-Schema Compilation Infoset</span></span>](../../../../docs/standard/data/xml/post-schema-compilation-infoset.md)
---
title: "Odwołanie do schematu kontraktu danych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b0838eeae79dff6e7f0371abe3a3ad23df0384a4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="230e9-102">Odwołanie do schematu kontraktu danych</span><span class="sxs-lookup"><span data-stu-id="230e9-102">Data Contract Schema Reference</span></span>
<span data-ttu-id="230e9-103">W tym temacie opisano podzestawu elementu schematu XML (XSD) używany przez <xref:System.Runtime.Serialization.DataContractSerializer> do opisywania wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) typy serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="230e9-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>  
  
## <a name="datacontractserializer-mappings"></a><span data-ttu-id="230e9-104">Mapowania DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="230e9-104">DataContractSerializer Mappings</span></span>  
 <span data-ttu-id="230e9-105">`DataContractSerializer` Typy CLR jest mapowany na XSD, gdy metadane są eksportowane z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi przy użyciu punktu końcowego metadanych lub [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="230e9-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="230e9-106">[Serializator kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span><span class="sxs-lookup"><span data-stu-id="230e9-106"> [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="230e9-107">`DataContractSerializer` Również mapuje XSD do typów CLR stosowania Svcutil.exe dostępu do sieci Web Services Description Language (WSDL) lub XSD dokumentów i generowanie kontraktów danych dotyczących usług i klientów.</span><span class="sxs-lookup"><span data-stu-id="230e9-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>  
  
 <span data-ttu-id="230e9-108">Schematu XML tylko te wystąpienia, które odpowiadają wymagania określone w tym dokumencie mogą być mapowane na typy CLR za pomocą funkcji `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="230e9-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>  
  
### <a name="support-levels"></a><span data-ttu-id="230e9-109">Poziomach pomocy technicznej</span><span class="sxs-lookup"><span data-stu-id="230e9-109">Support Levels</span></span>  
 <span data-ttu-id="230e9-110">`DataContractSerializer` Zawiera następujące poziomy wsparcia dla danej funkcji schematu XML:</span><span class="sxs-lookup"><span data-stu-id="230e9-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>  
  
-   <span data-ttu-id="230e9-111">**Obsługiwane**.</span><span class="sxs-lookup"><span data-stu-id="230e9-111">**Supported**.</span></span> <span data-ttu-id="230e9-112">Istnieje jawne mapowanie z tej funkcji CLR typy atrybutów (i/lub) przy użyciu `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="230e9-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>  
  
-   <span data-ttu-id="230e9-113">**Ignorowane**.</span><span class="sxs-lookup"><span data-stu-id="230e9-113">**Ignored**.</span></span> <span data-ttu-id="230e9-114">Funkcja jest dozwolona w schematach zaimportowanej przez `DataContractSerializer`, ale nie ma wpływu na generowanie kodu.</span><span class="sxs-lookup"><span data-stu-id="230e9-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>  
  
-   <span data-ttu-id="230e9-115">**Dostęp zabroniony**.</span><span class="sxs-lookup"><span data-stu-id="230e9-115">**Forbidden**.</span></span> <span data-ttu-id="230e9-116">`DataContractSerializer` Nie obsługuje importowania schematu za pomocą funkcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="230e9-117">Na przykład Svcutil.exe, podczas uzyskiwania dostępu do WSDL ze schematem, który korzysta z takich funkcji przełączy się <xref:System.Xml.Serialization.XmlSerializer> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="230e9-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="230e9-118">Jest to domyślnie.</span><span class="sxs-lookup"><span data-stu-id="230e9-118">This is by default.</span></span>  
  
## <a name="general-information"></a><span data-ttu-id="230e9-119">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="230e9-119">General Information</span></span>  
  
-   <span data-ttu-id="230e9-120">Przestrzeń nazw schematu jest w sposób opisany w [schematu XML](http://go.microsoft.com/fwlink/?LinkId=95475).</span><span class="sxs-lookup"><span data-stu-id="230e9-120">The schema namespace is described at [XML Schema](http://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="230e9-121">Prefiks "xs" jest używany w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="230e9-121">The prefix "xs" is used in this document.</span></span>  
  
-   <span data-ttu-id="230e9-122">Atrybuty z przestrzeni nazw z systemem innym niż schematu są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-122">Any attributes with a non-schema namespace are ignored.</span></span>  
  
-   <span data-ttu-id="230e9-123">Adnotacji (z wyjątkiem opisane w tym dokumencie) są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-123">Any annotations (except for those described in this document) are ignored.</span></span>  
  
### <a name="xsschema-attributes"></a><span data-ttu-id="230e9-124">\<xs:Schema >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-124">\<xs:schema>: attributes</span></span>  
  
|<span data-ttu-id="230e9-125">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-125">Attribute</span></span>|<span data-ttu-id="230e9-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="230e9-126">DataContract</span></span>|  
|---------------|------------------|  
|`attributeFormDefault`|<span data-ttu-id="230e9-127">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-127">Ignored.</span></span>|  
|`blockDefault`|<span data-ttu-id="230e9-128">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-128">Ignored.</span></span>|  
|`elementFormDefault`|<span data-ttu-id="230e9-129">Musi być kwalifikowany.</span><span class="sxs-lookup"><span data-stu-id="230e9-129">Must be qualified.</span></span> <span data-ttu-id="230e9-130">Wszystkie elementy musi być kwalifikowana dla schematu obsługiwany przez `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="230e9-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="230e9-131">Można to zrobić przez dowolnego z tych ustawień xs:schema/@elementFormDefault "kwalifikowana" lub przez ustawienie xs:element/@form do "kwalifikowana" dla każdej deklaracji pojedynczy element.</span><span class="sxs-lookup"><span data-stu-id="230e9-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|  
|`finalDefault`|<span data-ttu-id="230e9-132">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-132">Ignored.</span></span>|  
|`Id`|<span data-ttu-id="230e9-133">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-133">Ignored.</span></span>|  
|`targetNamespace`|<span data-ttu-id="230e9-134">Obsługiwane i mapowany na przestrzeń nazw kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="230e9-135">Jeśli ten atrybut nie jest określony, używana jest pusta przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="230e9-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="230e9-136">Nie może być http://schemas.microsoft.com/2003/10/Serialization/ zarezerwowaną przestrzenią nazw.</span><span class="sxs-lookup"><span data-stu-id="230e9-136">Cannot be the reserved namespace http://schemas.microsoft.com/2003/10/Serialization/.</span></span>|  
|`version`|<span data-ttu-id="230e9-137">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-137">Ignored.</span></span>|  
  
### <a name="xsschema-contents"></a><span data-ttu-id="230e9-138">\<xs:Schema >: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-138">\<xs:schema>: contents</span></span>  
  
|<span data-ttu-id="230e9-139">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-139">Contents</span></span>|<span data-ttu-id="230e9-140">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-140">Schema</span></span>|  
|--------------|------------|  
|`include`|<span data-ttu-id="230e9-141">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-141">Supported.</span></span> <span data-ttu-id="230e9-142">`DataContractSerializer`obsługuje xs: obejmują i xs:import.</span><span class="sxs-lookup"><span data-stu-id="230e9-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="230e9-143">Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się po załadowaniu metadanych z pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="230e9-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="230e9-144">Lista plików schematów muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pomocą `include` w takim przypadku; `include`d schematu dokumentów są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`redefine`|<span data-ttu-id="230e9-145">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-145">Forbidden.</span></span> <span data-ttu-id="230e9-146">Korzystanie z `xs:redefine` jest zabronione przez `DataContractSerializer` ze względów bezpieczeństwa: `x:redefine` wymaga `schemaLocation` postępowania.</span><span class="sxs-lookup"><span data-stu-id="230e9-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="230e9-147">W pewnych okolicznościach Svcutil.exe przy użyciu obiektu DataContract ogranicza użycie `schemaLocation`.</span><span class="sxs-lookup"><span data-stu-id="230e9-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|  
|`import`|<span data-ttu-id="230e9-148">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-148">Supported.</span></span> <span data-ttu-id="230e9-149">`DataContractSerializer`obsługuje `xs:include` i `xs:import`.</span><span class="sxs-lookup"><span data-stu-id="230e9-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="230e9-150">Jednak ogranicza Svcutil.exe następujące `xs:include/@schemaLocation` i `xs:import/@location` odwołuje się po załadowaniu metadanych z pliku lokalnego.</span><span class="sxs-lookup"><span data-stu-id="230e9-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="230e9-151">Lista plików schematów muszą być przekazywane za pośrednictwem mechanizmu poza pasmem, a nie za pomocą `include` w takim przypadku; `include`d schematu dokumentów są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`simpleType`|<span data-ttu-id="230e9-152">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-152">Supported.</span></span> <span data-ttu-id="230e9-153">Zobacz `xs:simpleType` sekcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-153">See the `xs:simpleType` section.</span></span>|  
|`complexType`|<span data-ttu-id="230e9-154">Obsługiwane, map do kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="230e9-155">Zobacz `xs:complexType` sekcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-155">See the `xs:complexType` section.</span></span>|  
|`group`|<span data-ttu-id="230e9-156">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-156">Ignored.</span></span> <span data-ttu-id="230e9-157">`DataContractSerializer`nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="230e9-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="230e9-158">Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie można odwoływać się za pomocą `complexType` lub inne konstrukcje obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`attributeGroup`|<span data-ttu-id="230e9-159">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-159">Ignored.</span></span> <span data-ttu-id="230e9-160">`DataContractSerializer`nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="230e9-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="230e9-161">Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie można odwoływać się za pomocą `complexType` lub inne konstrukcje obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`element`|<span data-ttu-id="230e9-162">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-162">Supported.</span></span> <span data-ttu-id="230e9-163">Zobacz Element globalny deklaracji (e).</span><span class="sxs-lookup"><span data-stu-id="230e9-163">See Global Element Declaration (GED).</span></span>|  
|`attribute`|<span data-ttu-id="230e9-164">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-164">Ignored.</span></span> <span data-ttu-id="230e9-165">`DataContractSerializer`nie obsługuje użycia `xs:group`, `xs:attributeGroup`, i `xs:attribute`.</span><span class="sxs-lookup"><span data-stu-id="230e9-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="230e9-166">Deklaracje te są ignorowane jako elementy podrzędne `xs:schema`, ale nie można odwoływać się za pomocą `complexType` lub inne konstrukcje obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`notation`|<span data-ttu-id="230e9-167">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-167">Ignored.</span></span>|  
  
## <a name="complex-types--xscomplextype"></a><span data-ttu-id="230e9-168">Typy złożone — \<xs:complexType ></span><span class="sxs-lookup"><span data-stu-id="230e9-168">Complex Types – \<xs:complexType></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="230e9-169">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="230e9-169">General Information</span></span>  
 <span data-ttu-id="230e9-170">Każdy typ złożony \<xs:complexType > mapuje kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>  
  
### <a name="xscomplextype-attributes"></a><span data-ttu-id="230e9-171">\<xs:complexType >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-171">\<xs:complexType>: attributes</span></span>  
  
|<span data-ttu-id="230e9-172">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-172">Attribute</span></span>|<span data-ttu-id="230e9-173">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-173">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="230e9-174">Musi mieć wartość FAŁSZ (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="230e9-174">Must be false (default).</span></span>|  
|`block`|<span data-ttu-id="230e9-175">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-175">Forbidden.</span></span>|  
|`final`|<span data-ttu-id="230e9-176">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-176">Ignored.</span></span>|  
|`id`|<span data-ttu-id="230e9-177">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-177">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="230e9-178">Musi mieć wartość FAŁSZ (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="230e9-178">Must be false (default).</span></span>|  
|`name`|<span data-ttu-id="230e9-179">Obsługiwane i zamapowany na nazwę kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="230e9-180">Jeśli istnieją kropki w nazwie, podejmowana jest próba mapowania typu na typ wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="230e9-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="230e9-181">Na przykład typu złożonego o nazwie `A.B` map do kontraktu danych typ wewnętrzny typ typu o nazwie kontraktu danych `A`, ale tylko wtedy, gdy typ kontraktu tych danych istnieje.</span><span class="sxs-lookup"><span data-stu-id="230e9-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="230e9-182">Możliwe jest więcej niż jeden poziom zagnieżdżenia: na przykład `A.B.C` może być typu wewnętrznego, ale tylko wtedy, gdy `A` i `A.B` istnieją.</span><span class="sxs-lookup"><span data-stu-id="230e9-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|  
  
### <a name="xscomplextype-contents"></a><span data-ttu-id="230e9-183">\<xs:complexType >: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-183">\<xs:complexType>: contents</span></span>  
  
|<span data-ttu-id="230e9-184">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-184">Contents</span></span>|<span data-ttu-id="230e9-185">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-185">Schema</span></span>|  
|--------------|------------|  
|`simpleContent`|<span data-ttu-id="230e9-186">Rozszerzenia są zabronione.</span><span class="sxs-lookup"><span data-stu-id="230e9-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="230e9-187">Ograniczenie jest dozwolone tylko w `anySimpleType`.</span><span class="sxs-lookup"><span data-stu-id="230e9-187">Restriction is allowed only from `anySimpleType`.</span></span>|  
|`complexContent`|<span data-ttu-id="230e9-188">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-188">Supported.</span></span> <span data-ttu-id="230e9-189">Zobacz "Dziedziczenia".</span><span class="sxs-lookup"><span data-stu-id="230e9-189">See "Inheritance".</span></span>|  
|`group`|<span data-ttu-id="230e9-190">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-190">Forbidden.</span></span>|  
|`all`|<span data-ttu-id="230e9-191">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-191">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="230e9-192">Dostęp zabroniony</span><span class="sxs-lookup"><span data-stu-id="230e9-192">Forbidden</span></span>|  
|`sequence`|<span data-ttu-id="230e9-193">Obsługiwane, mapy do elementów członkowskich danych kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-193">Supported, maps to data members of a data contract.</span></span>|  
|`attribute`|<span data-ttu-id="230e9-194">Dostęp jest zabroniony, nawet jeśli Użyj = "prohibited" (z wyjątkiem jednego).</span><span class="sxs-lookup"><span data-stu-id="230e9-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="230e9-195">Obsługiwane są tylko opcjonalne atrybuty z przestrzeni nazw standardowe schematu serializacji.</span><span class="sxs-lookup"><span data-stu-id="230e9-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="230e9-196">Nie są mapowane na elementy członkowskie danych w modelu programowania kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="230e9-197">Obecnie tylko jeden taki atrybut ma znaczenie i została szczegółowo opisana w sekcji ISerializable.</span><span class="sxs-lookup"><span data-stu-id="230e9-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="230e9-198">Wszystkie pozostałe są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-198">All others are ignored.</span></span>|  
|`attributeGroup`|<span data-ttu-id="230e9-199">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-199">Forbidden.</span></span> <span data-ttu-id="230e9-200">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wersji v1 `DataContractSerializer` ignoruje obecności `attributeGroup` wewnątrz `xs:complexType`.</span><span class="sxs-lookup"><span data-stu-id="230e9-200">In the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|  
|`anyAttribute`|<span data-ttu-id="230e9-201">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-201">Forbidden.</span></span>|  
|<span data-ttu-id="230e9-202">(pusta)</span><span class="sxs-lookup"><span data-stu-id="230e9-202">(empty)</span></span>|<span data-ttu-id="230e9-203">Mapowany do kontraktu danych z żadnych elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-203">Maps to a data contract with no data members.</span></span>|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="230e9-204">\<użyto > w typie złożonym: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-204">\<xs:sequence> in a complex type: attributes</span></span>  
  
|<span data-ttu-id="230e9-205">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-205">Attribute</span></span>|<span data-ttu-id="230e9-206">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-206">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="230e9-207">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-207">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="230e9-208">Musi mieć wartość 1 (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="230e9-208">Must be 1 (default).</span></span>|  
|`minOccurs`|<span data-ttu-id="230e9-209">Musi mieć wartość 1 (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="230e9-209">Must be 1 (default).</span></span>|  
  
### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="230e9-210">\<użyto > w typie złożonym: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-210">\<xs:sequence> in a complex type: contents</span></span>  
  
|<span data-ttu-id="230e9-211">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-211">Contents</span></span>|<span data-ttu-id="230e9-212">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-212">Schema</span></span>|  
|--------------|------------|  
|`element`|<span data-ttu-id="230e9-213">Każde wystąpienie mapuje do elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-213">Each instance maps to a data member.</span></span>|  
|`group`|<span data-ttu-id="230e9-214">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-214">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="230e9-215">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-215">Forbidden.</span></span>|  
|`sequence`|<span data-ttu-id="230e9-216">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-216">Forbidden.</span></span>|  
|`any`|<span data-ttu-id="230e9-217">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-217">Forbidden.</span></span>|  
|<span data-ttu-id="230e9-218">(pusta)</span><span class="sxs-lookup"><span data-stu-id="230e9-218">(empty)</span></span>|<span data-ttu-id="230e9-219">Mapowany do kontraktu danych z żadnych elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-219">Maps to a data contract with no data members.</span></span>|  
  
## <a name="elements--xselement"></a><span data-ttu-id="230e9-220">Elementy — \<elementu xs: element ></span><span class="sxs-lookup"><span data-stu-id="230e9-220">Elements – \<xs:element></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="230e9-221">Informacje ogólne</span><span class="sxs-lookup"><span data-stu-id="230e9-221">General Information</span></span>  
 <span data-ttu-id="230e9-222">`<xs:element>`może wystąpić w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="230e9-222">`<xs:element>` can occur in the following contexts:</span></span>  
  
-   <span data-ttu-id="230e9-223">Może wystąpić w `<xs:sequence>`, która opisuje element członkowski danych klasy kontraktu regularnych danych (z systemem innym niż kolekcji).</span><span class="sxs-lookup"><span data-stu-id="230e9-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="230e9-224">W takim przypadku `maxOccurs` atrybutu musi być równa 1.</span><span class="sxs-lookup"><span data-stu-id="230e9-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="230e9-225">(Wartość 0 nie jest dozwolona).</span><span class="sxs-lookup"><span data-stu-id="230e9-225">(A value of 0 is not allowed).</span></span>  
  
-   <span data-ttu-id="230e9-226">Może wystąpić w `<xs:sequence>`, która opisuje element członkowski danych klasy kontraktu danych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="230e9-227">W takim przypadku `maxOccurs` atrybutu musi być większa niż 1 lub "unbounded".</span><span class="sxs-lookup"><span data-stu-id="230e9-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>  
  
-   <span data-ttu-id="230e9-228">Może wystąpić w `<xs:schema>` jako globalny Element deklaracji (e).</span><span class="sxs-lookup"><span data-stu-id="230e9-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="230e9-229">\<elementu xs: element > maxOccurs = 1 w \<użyto > (elementy członkowskie danych)</span><span class="sxs-lookup"><span data-stu-id="230e9-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>  
  
|<span data-ttu-id="230e9-230">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-230">Attribute</span></span>|<span data-ttu-id="230e9-231">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-231">Schema</span></span>|  
|---------------|------------|  
|`ref`|<span data-ttu-id="230e9-232">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-232">Forbidden.</span></span>|  
|`name`|<span data-ttu-id="230e9-233">Obsługiwane mapowana na nazwę elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-233">Supported, maps to the data member name.</span></span>|  
|`type`|<span data-ttu-id="230e9-234">Obsługiwane, typu map do elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="230e9-235">Aby uzyskać więcej informacji zobacz Mapowanie typu/typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="230e9-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="230e9-236">Jeśli nie określono (i element nie zawiera typu anonimowego) `xs:anyType` zakłada, że.</span><span class="sxs-lookup"><span data-stu-id="230e9-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|  
|`block`|<span data-ttu-id="230e9-237">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-237">Ignored.</span></span>|  
|`default`|<span data-ttu-id="230e9-238">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-238">Forbidden.</span></span>|  
|`fixed`|<span data-ttu-id="230e9-239">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-239">Forbidden.</span></span>|  
|`form`|<span data-ttu-id="230e9-240">Musi być kwalifikowany.</span><span class="sxs-lookup"><span data-stu-id="230e9-240">Must be qualified.</span></span> <span data-ttu-id="230e9-241">Ten atrybut można określać za pośrednictwem `elementFormDefault` na `xs:schema`.</span><span class="sxs-lookup"><span data-stu-id="230e9-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|  
|`id`|<span data-ttu-id="230e9-242">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-242">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="230e9-243">1</span><span class="sxs-lookup"><span data-stu-id="230e9-243">1</span></span>|  
|`minOccurs`|<span data-ttu-id="230e9-244">Mapuje <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> właściwości elementu członkowskiego danych (`IsRequired` ma wartość true, gdy `minOccurs` 1).</span><span class="sxs-lookup"><span data-stu-id="230e9-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|  
|`nillable`|<span data-ttu-id="230e9-245">Mapowanie typu wpływ.</span><span class="sxs-lookup"><span data-stu-id="230e9-245">Affects type mapping.</span></span> <span data-ttu-id="230e9-246">Zobacz Mapowanie typu/typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="230e9-246">See Type/primitive mapping.</span></span>|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="230e9-247">\<elementu xs: element > z maxOccurs > 1 \<użyto > (kolekcji)</span><span class="sxs-lookup"><span data-stu-id="230e9-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>  
  
-   <span data-ttu-id="230e9-248">Mapuje <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="230e9-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>  
  
-   <span data-ttu-id="230e9-249">Typy kolekcji tylko jednego elementu xs: element jest dozwolone w ramach użyto.</span><span class="sxs-lookup"><span data-stu-id="230e9-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>  
  
 <span data-ttu-id="230e9-250">Kolekcje mogą być następujące:</span><span class="sxs-lookup"><span data-stu-id="230e9-250">Collections can be of the following types:</span></span>  
  
-   <span data-ttu-id="230e9-251">Kolekcje regularne (na przykład tablice).</span><span class="sxs-lookup"><span data-stu-id="230e9-251">Regular collections (for example, arrays).</span></span>  
  
-   <span data-ttu-id="230e9-252">Kolekcje słownika (mapowanie jeden wartość; na przykład <xref:System.Collections.Hashtable>).</span><span class="sxs-lookup"><span data-stu-id="230e9-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>  
  
-   <span data-ttu-id="230e9-253">Jedyną różnicą między słownika i tablicy typu pary klucz wartość znajduje się w wygenerowanym modelu programowania.</span><span class="sxs-lookup"><span data-stu-id="230e9-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="230e9-254">Istnieje mechanizm adnotacji schemat, który może służyć do wskazywania danego typu kolekcji słownika.</span><span class="sxs-lookup"><span data-stu-id="230e9-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>  
  
 <span data-ttu-id="230e9-255">Zasady `ref`, `block`, `default`, `fixed`, `form`, i `id` atrybuty są takie same jak w przypadku — do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="230e9-256">Inne atrybuty zawiera w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="230e9-256">Other attributes include those in the following table.</span></span>  
  
|<span data-ttu-id="230e9-257">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-257">Attribute</span></span>|<span data-ttu-id="230e9-258">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-258">Schema</span></span>|  
|---------------|------------|  
|`name`|<span data-ttu-id="230e9-259">Obsługiwane map do <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> właściwości w `CollectionDataContractAttribute` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="230e9-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|  
|`type`|<span data-ttu-id="230e9-260">Obsługiwane mapowana na typie przechowywane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-260">Supported, maps to the type stored in the collection.</span></span>|  
|`maxOccurs`|<span data-ttu-id="230e9-261">Większa niż 1 lub "unbounded".</span><span class="sxs-lookup"><span data-stu-id="230e9-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="230e9-262">Schemat kontrolera domeny, należy użyć "unbounded".</span><span class="sxs-lookup"><span data-stu-id="230e9-262">The DC schema should use "unbounded".</span></span>|  
|`minOccurs`|<span data-ttu-id="230e9-263">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-263">Ignored.</span></span>|  
|`nillable`|<span data-ttu-id="230e9-264">Mapowanie typu wpływ.</span><span class="sxs-lookup"><span data-stu-id="230e9-264">Affects type mapping.</span></span> <span data-ttu-id="230e9-265">Ten atrybut jest ignorowany dla kolekcji słownika.</span><span class="sxs-lookup"><span data-stu-id="230e9-265">This attribute is ignored for dictionary collections.</span></span>|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="230e9-266">\<elementu xs: element > w \<xs:schema > globalne deklarację elementu</span><span class="sxs-lookup"><span data-stu-id="230e9-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>  
  
-   <span data-ttu-id="230e9-267">Globalny Element deklaracji (e) jako typu w schemacie, który ma taką samą nazwę i przestrzeń nazw lub definiujący typu anonimowego wewnątrz, jest określany jako skojarzone z typem.</span><span class="sxs-lookup"><span data-stu-id="230e9-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>  
  
-   <span data-ttu-id="230e9-268">Eksportowania schematu: GEDs skojarzone są generowane dla każdego typu wygenerowanego, zarówno proste i złożone.</span><span class="sxs-lookup"><span data-stu-id="230e9-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>  
  
-   <span data-ttu-id="230e9-269">Serializacji/deserializacji: GEDs skojarzone są używane jako elementy główne dla typu.</span><span class="sxs-lookup"><span data-stu-id="230e9-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>  
  
-   <span data-ttu-id="230e9-270">Importowanie schematu: skojarzony GEDs nie są wymagane i są ignorowane, jeśli następujące reguły są zgodne (chyba że są one Definiowanie typów).</span><span class="sxs-lookup"><span data-stu-id="230e9-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>  
  
|<span data-ttu-id="230e9-271">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-271">Attribute</span></span>|<span data-ttu-id="230e9-272">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-272">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="230e9-273">Musi mieć wartość false dla GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-273">Must be false for associated GEDs.</span></span>|  
|`block`|<span data-ttu-id="230e9-274">Jest zabronione w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-274">Forbidden in associated GEDs.</span></span>|  
|`default`|<span data-ttu-id="230e9-275">Jest zabronione w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-275">Forbidden in associated GEDs.</span></span>|  
|`final`|<span data-ttu-id="230e9-276">Musi mieć wartość false dla GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-276">Must be false for associated GEDs.</span></span>|  
|`fixed`|<span data-ttu-id="230e9-277">Jest zabronione w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-277">Forbidden in associated GEDs.</span></span>|  
|`id`|<span data-ttu-id="230e9-278">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-278">Ignored.</span></span>|  
|`name`|<span data-ttu-id="230e9-279">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-279">Supported.</span></span> <span data-ttu-id="230e9-280">Patrz definicja GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-280">See the definition of associated GEDs.</span></span>|  
|`nillable`|<span data-ttu-id="230e9-281">Musi mieć wartość true dla GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-281">Must be true for associated GEDs.</span></span>|  
|`substitutionGroup`|<span data-ttu-id="230e9-282">Jest zabronione w GEDs skojarzone.</span><span class="sxs-lookup"><span data-stu-id="230e9-282">Forbidden in associated GEDs.</span></span>|  
|`type`|<span data-ttu-id="230e9-283">Obsługiwane i musi odpowiadać typowi skojarzone dla skojarzonego GEDs (chyba, że element zawiera typu anonimowego).</span><span class="sxs-lookup"><span data-stu-id="230e9-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|  
  
### <a name="xselement-contents"></a><span data-ttu-id="230e9-284">\<elementu xs: element >: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-284">\<xs:element>: contents</span></span>  
  
|<span data-ttu-id="230e9-285">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-285">Contents</span></span>|<span data-ttu-id="230e9-286">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-286">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="230e9-287">Supported.*</span><span class="sxs-lookup"><span data-stu-id="230e9-287">Supported.*</span></span>|  
|`complexType`|<span data-ttu-id="230e9-288">Supported.*</span><span class="sxs-lookup"><span data-stu-id="230e9-288">Supported.*</span></span>|  
|`unique`|<span data-ttu-id="230e9-289">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-289">Ignored.</span></span>|  
|`key`|<span data-ttu-id="230e9-290">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-290">Ignored.</span></span>|  
|`keyref`|<span data-ttu-id="230e9-291">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-291">Ignored.</span></span>|  
|<span data-ttu-id="230e9-292">(pusty)</span><span class="sxs-lookup"><span data-stu-id="230e9-292">(blank)</span></span>|<span data-ttu-id="230e9-293">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-293">Supported.</span></span>|  
  
 <span data-ttu-id="230e9-294">\*Korzystając z `simpleType` i `complexType,` mapowania typów anonimowych są takie same jak typy nieanonimowych z tą różnicą, że nie istnieje żaden kontrakt anonimowe dane, w związku z czym kontrakt danych o podanej nazwie jest tworzony z nazwą wygenerowanego pochodzi od nazwy elementu.</span><span class="sxs-lookup"><span data-stu-id="230e9-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="230e9-295">Zasady dla typów anonimowych są na poniższej liście:</span><span class="sxs-lookup"><span data-stu-id="230e9-295">The rules for anonymous types are in the following list:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="230e9-296">Szczegóły implementacji: Jeśli `xs:element` nazwa nie zawiera okresów, mapy typu anonimowego na wewnętrzny typ typu kontraktu danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="230e9-296"> implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="230e9-297">Jeśli nazwa zawiera okresów, wynikowy typ kontraktu danych jest niezależna (nie wewnętrzny typ).</span><span class="sxs-lookup"><span data-stu-id="230e9-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>  
  
-   <span data-ttu-id="230e9-298">Nazwa kontraktu danych wygenerowanych wewnętrzny typu jest nazwą kontraktu danych typu zewnętrznego, a następnie kropką, nazwę elementu i ciągu "Type".</span><span class="sxs-lookup"><span data-stu-id="230e9-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>  
  
-   <span data-ttu-id="230e9-299">Kontraktu danych o takiej nazwie już istnieje, nazwa ma zostać unikatowy przez dołączenie "1", "2", "3", i tak dalej do momentu utworzenia unikatowej nazwy.</span><span class="sxs-lookup"><span data-stu-id="230e9-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>  
  
## <a name="simple-types---xssimpletype"></a><span data-ttu-id="230e9-300">Proste typy - \<xs:simpleType ></span><span class="sxs-lookup"><span data-stu-id="230e9-300">Simple Types - \<xs:simpleType></span></span>  
  
### <a name="xssimpletype-attributes"></a><span data-ttu-id="230e9-301">\<xs:simpleType >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-301">\<xs:simpleType>: attributes</span></span>  
  
|<span data-ttu-id="230e9-302">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-302">Attribute</span></span>|<span data-ttu-id="230e9-303">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-303">Schema</span></span>|  
|---------------|------------|  
|`final`|<span data-ttu-id="230e9-304">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-304">Ignored.</span></span>|  
|`id`|<span data-ttu-id="230e9-305">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-305">Ignored.</span></span>|  
|`name`|<span data-ttu-id="230e9-306">Obsługiwane, mapy danych nazwę kontraktu.</span><span class="sxs-lookup"><span data-stu-id="230e9-306">Supported, maps to the data contract name.</span></span>|  
  
### <a name="xssimpletype-contents"></a><span data-ttu-id="230e9-307">\<xs:simpleType >: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-307">\<xs:simpleType>: contents</span></span>  
  
|<span data-ttu-id="230e9-308">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-308">Contents</span></span>|<span data-ttu-id="230e9-309">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-309">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="230e9-310">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-310">Supported.</span></span> <span data-ttu-id="230e9-311">Mapowany do kontraktów danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="230e9-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="230e9-312">Ten atrybut jest ignorowana, jeśli nie jest zgodny ze wzorcem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="230e9-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="230e9-313">Zobacz `xs:simpleType` sekcji ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="230e9-313">See the `xs:simpleType` restrictions section.</span></span>|  
|`list`|<span data-ttu-id="230e9-314">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-314">Supported.</span></span> <span data-ttu-id="230e9-315">Mapuje Flaga kontraktów danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="230e9-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="230e9-316">Zobacz `xs:simpleType` wymieniono sekcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-316">See the `xs:simpleType` lists section.</span></span>|  
|`union`|<span data-ttu-id="230e9-317">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-317">Forbidden.</span></span>|  
  
### <a name="xsrestriction"></a><span data-ttu-id="230e9-318">\<xs:restriction ></span><span class="sxs-lookup"><span data-stu-id="230e9-318">\<xs:restriction></span></span>  
  
-   <span data-ttu-id="230e9-319">Ograniczenia typu złożonego są obsługiwane tylko dla podstawy = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="230e9-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>  
  
-   <span data-ttu-id="230e9-320">Ograniczenia typu prostego `xs:string` nie mają żadnych ograniczeń aspekty inne niż `xs:enumeration` są mapowane na wyliczenie kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>  
  
-   <span data-ttu-id="230e9-321">Wszystkie inne ograniczenia typu prostego są mapowane na typy, które ograniczają one.</span><span class="sxs-lookup"><span data-stu-id="230e9-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="230e9-322">Na przykład ograniczenia `xs:int` mapowana na liczbę całkowitą, podobnie jak `xs:int` sam przeprowadza.</span><span class="sxs-lookup"><span data-stu-id="230e9-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="230e9-323">typ pierwotny mapowania, zobacz Mapowanie typu/typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="230e9-323"> primitive type mapping, see Type/primitive mapping.</span></span>  
  
### <a name="xsrestriction-attributes"></a><span data-ttu-id="230e9-324">\<xs:restriction >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-324">\<xs:restriction>: attributes</span></span>  
  
|<span data-ttu-id="230e9-325">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-325">Attribute</span></span>|<span data-ttu-id="230e9-326">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-326">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="230e9-327">Musi być typem prostym obsługiwanych lub `xs:anyType`.</span><span class="sxs-lookup"><span data-stu-id="230e9-327">Must be a supported simple type or `xs:anyType`.</span></span>|  
|`id`|<span data-ttu-id="230e9-328">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-328">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="230e9-329">\<xs:restriction > dla wszystkich innych przypadkach: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-329">\<xs:restriction> for all other cases: contents</span></span>  
  
|<span data-ttu-id="230e9-330">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-330">Contents</span></span>|<span data-ttu-id="230e9-331">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-331">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="230e9-332">Jeśli jest obecny, musi pochodzić z nieobsługiwanym typem pierwotnym.</span><span class="sxs-lookup"><span data-stu-id="230e9-332">If present, must be derived from a supported primitive type.</span></span>|  
|`minExclusive`|<span data-ttu-id="230e9-333">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-333">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="230e9-334">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-334">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="230e9-335">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-335">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="230e9-336">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-336">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="230e9-337">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-337">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="230e9-338">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-338">Ignored.</span></span>|  
|`length`|<span data-ttu-id="230e9-339">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-339">Ignored.</span></span>|  
|`minLength`|<span data-ttu-id="230e9-340">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-340">Ignored.</span></span>|  
|`maxLength`|<span data-ttu-id="230e9-341">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-341">Ignored.</span></span>|  
|`enumeration`|<span data-ttu-id="230e9-342">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-342">Ignored.</span></span>|  
|`whiteSpace`|<span data-ttu-id="230e9-343">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-343">Ignored.</span></span>|  
|`pattern`|<span data-ttu-id="230e9-344">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-344">Ignored.</span></span>|  
|<span data-ttu-id="230e9-345">(pusty)</span><span class="sxs-lookup"><span data-stu-id="230e9-345">(blank)</span></span>|<span data-ttu-id="230e9-346">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-346">Supported.</span></span>|  
  
## <a name="enumeration"></a><span data-ttu-id="230e9-347">Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="230e9-347">Enumeration</span></span>  
  
### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="230e9-348">\<xs:restriction > dla wyliczenia: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-348">\<xs:restriction> for enumerations: attributes</span></span>  
  
|<span data-ttu-id="230e9-349">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-349">Attribute</span></span>|<span data-ttu-id="230e9-350">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-350">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="230e9-351">Jeśli jest obecny, musi być `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="230e9-351">If present, must be `xs:string`.</span></span>|  
|`id`|<span data-ttu-id="230e9-352">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-352">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="230e9-353">\<xs:restriction > dla wyliczenia: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-353">\<xs:restriction> for enumerations: contents</span></span>  
  
|<span data-ttu-id="230e9-354">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-354">Contents</span></span>|<span data-ttu-id="230e9-355">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-355">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="230e9-356">Jeśli jest obecny, musi być ograniczenia wyliczenia obsługiwana przez kontrakt danych (w tej sekcji).</span><span class="sxs-lookup"><span data-stu-id="230e9-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|  
|`minExclusive`|<span data-ttu-id="230e9-357">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-357">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="230e9-358">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-358">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="230e9-359">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-359">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="230e9-360">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-360">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="230e9-361">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-361">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="230e9-362">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-362">Ignored.</span></span>|  
|`length`|<span data-ttu-id="230e9-363">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-363">Forbidden.</span></span>|  
|`minLength`|<span data-ttu-id="230e9-364">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-364">Forbidden.</span></span>|  
|`maxLength`|<span data-ttu-id="230e9-365">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-365">Forbidden.</span></span>|  
|`enumeration`|<span data-ttu-id="230e9-366">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-366">Supported.</span></span> <span data-ttu-id="230e9-367">Wyliczenie "id" zostanie zignorowany, a "wartość" mapuje nazwę wartości wyliczenia umowy danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|  
|`whiteSpace`|<span data-ttu-id="230e9-368">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-368">Forbidden.</span></span>|  
|`pattern`|<span data-ttu-id="230e9-369">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-369">Forbidden.</span></span>|  
|<span data-ttu-id="230e9-370">(pusta)</span><span class="sxs-lookup"><span data-stu-id="230e9-370">(empty)</span></span>|<span data-ttu-id="230e9-371">Obsługiwane, mapy na typ wyliczeniowy puste.</span><span class="sxs-lookup"><span data-stu-id="230e9-371">Supported, maps to empty enumeration type.</span></span>|  
  
 <span data-ttu-id="230e9-372">Poniższy kod przedstawia klasy wyliczenie C#.</span><span class="sxs-lookup"><span data-stu-id="230e9-372">The following code shows a C# enumeration class.</span></span>  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 <span data-ttu-id="230e9-373">}</span><span class="sxs-lookup"><span data-stu-id="230e9-373">}</span></span>  
  
 <span data-ttu-id="230e9-374">Ta klasa mapuje następującego schematu przez `DataContractSerializer`.</span><span class="sxs-lookup"><span data-stu-id="230e9-374">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="230e9-375">Jeśli wartości wyliczenia można uruchomić z zakresu od 1, `xs:annotation` bloków nie zostały wygenerowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-375">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a><span data-ttu-id="230e9-376">\<xs:list ></span><span class="sxs-lookup"><span data-stu-id="230e9-376">\<xs:list></span></span>  
 <span data-ttu-id="230e9-377">`DataContractSerializer`Typy wyliczeniowe mapy oznaczonych `System.FlagsAttribute` do `xs:list` pochodną `xs:string`.</span><span class="sxs-lookup"><span data-stu-id="230e9-377">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="230e9-378">Żaden inny `xs:list` zmian są obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-378">No other `xs:list` variations are supported.</span></span>  
  
### <a name="xslist-attributes"></a><span data-ttu-id="230e9-379">\<xs:list >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-379">\<xs:list>: attributes</span></span>  
  
|<span data-ttu-id="230e9-380">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-380">Attribute</span></span>|<span data-ttu-id="230e9-381">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-381">Schema</span></span>|  
|---------------|------------|  
|`itemType`|<span data-ttu-id="230e9-382">Dostęp jest zabroniony.</span><span class="sxs-lookup"><span data-stu-id="230e9-382">Forbidden.</span></span>|  
|`id`|<span data-ttu-id="230e9-383">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-383">Ignored.</span></span>|  
  
### <a name="xslist-contents"></a><span data-ttu-id="230e9-384">\<xs:list >: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-384">\<xs:list>: contents</span></span>  
  
|<span data-ttu-id="230e9-385">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-385">Contents</span></span>|<span data-ttu-id="230e9-386">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-386">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="230e9-387">Musi być ograniczenia z `xs:string` przy użyciu `xs:enumeration` zestawu reguł.</span><span class="sxs-lookup"><span data-stu-id="230e9-387">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|  
  
 <span data-ttu-id="230e9-388">Jeśli wartość wyliczenia nie jest zgodna z potęgą liczby 2 postępu (domyślnie flagi), wartość jest przechowywana w `xs:annotation/xs:appInfo/ser:EnumerationValue` elementu.</span><span class="sxs-lookup"><span data-stu-id="230e9-388">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>  
  
 <span data-ttu-id="230e9-389">Na przykład następujący kod flagi typem wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="230e9-389">For example, the following code flags an enumeration type.</span></span>  
  
```  
[Flags]  
public enum AuthFlags  
{    
  AuthAnonymous = 1,  
  AuthBasic = 2,  
  AuthNTLM = 4,  
  AuthMD5 = 16,  
  AuthWindowsLiveID = 64,  
}  
```  
  
 <span data-ttu-id="230e9-390">Ten typ jest mapowany na następującego schematu.</span><span class="sxs-lookup"><span data-stu-id="230e9-390">This type maps to the following schema.</span></span>  
  
```xml  
<xs:simpleType name="AuthFlags">  
    <xs:list>  
      <xs:simpleType>  
        <xs:restriction base="xs:string">  
          <xs:enumeration value="AuthAnonymous" />  
          <xs:enumeration value="AuthBasic" />  
          <xs:enumeration value="AuthNTLM" />  
          <xs:enumeration value="AuthMD5">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a><span data-ttu-id="230e9-391">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="230e9-391">Inheritance</span></span>  
  
### <a name="general-rules"></a><span data-ttu-id="230e9-392">Ogólne zasady</span><span class="sxs-lookup"><span data-stu-id="230e9-392">General rules</span></span>  
 <span data-ttu-id="230e9-393">Kontrakt danych może dziedziczyć z innego kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-393">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="230e9-394">Takie kontraktów danych mapowania do podstawowej i są uzyskiwane przez typy rozszerzeń przy użyciu `<xs:extension>` konstrukcja schematu XML.</span><span class="sxs-lookup"><span data-stu-id="230e9-394">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>  
  
 <span data-ttu-id="230e9-395">Kontrakt danych nie może dziedziczyć kontraktu danych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="230e9-395">A data contract cannot inherit from a collection data contract.</span></span>  
  
 <span data-ttu-id="230e9-396">Na przykład następujący kod jest kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-396">For example, the following code is a data contract.</span></span>  
  
```  
[DataContract]  
public class Person  
{  
  [DataMember]  
  public string Name;  
}  
[DataContract]  
public class Employee : Person   
{      
  [DataMember]  
  public int ID;  
}  
```  
  
 <span data-ttu-id="230e9-397">Mapuje tego kontraktu danych do następujących deklaracji typu schematu XML.</span><span class="sxs-lookup"><span data-stu-id="230e9-397">This data contract maps to the following XML Schema type declaration.</span></span>  
  
```xml  
<xs:complexType name="Employee">  
 <xs:complexContent mixed="false">  
  <xs:extension base="tns:Person">  
   <xs:sequence>  
    <xs:element minOccurs="0" name="ID" type="xs:int"/>  
   </xs:sequence>  
  </xs:extension>  
 </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="Person">  
 <xs:sequence>  
  <xs:element minOccurs="0" name="Name"   
    nillable="true" type="xs:string"/>  
 </xs:sequence>  
</xs:complexType>  
```  
  
### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="230e9-398">\<xs:complexContent >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-398">\<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="230e9-399">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-399">Attribute</span></span>|<span data-ttu-id="230e9-400">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-400">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="230e9-401">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-401">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="230e9-402">Musi mieć wartość false.</span><span class="sxs-lookup"><span data-stu-id="230e9-402">Must be false.</span></span>|  
  
### <a name="xscomplexcontent-contents"></a><span data-ttu-id="230e9-403">\<xs:complexContent >: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-403">\<xs:complexContent>: contents</span></span>  
  
|<span data-ttu-id="230e9-404">Spis treści</span><span class="sxs-lookup"><span data-stu-id="230e9-404">Contents</span></span>|<span data-ttu-id="230e9-405">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-405">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="230e9-406">Dostęp jest zabroniony, o ile podstawowy = "`xs:anyType`".</span><span class="sxs-lookup"><span data-stu-id="230e9-406">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="230e9-407">Nie jest odpowiednikiem umieszczenie zawartość `xs:restriction` bezpośrednio w kontenerze `xs:complexContent`.</span><span class="sxs-lookup"><span data-stu-id="230e9-407">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|  
|`extension`|<span data-ttu-id="230e9-408">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-408">Supported.</span></span> <span data-ttu-id="230e9-409">Mapowany do Dziedziczenie kontraktów danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-409">Maps to data contract inheritance.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="230e9-410">\<xs:Extension > w \<xs:complexContent >: atrybuty</span><span class="sxs-lookup"><span data-stu-id="230e9-410">\<xs:extension> in \<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="230e9-411">Atrybut</span><span class="sxs-lookup"><span data-stu-id="230e9-411">Attribute</span></span>|<span data-ttu-id="230e9-412">Schemat</span><span class="sxs-lookup"><span data-stu-id="230e9-412">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="230e9-413">Ignorowane.</span><span class="sxs-lookup"><span data-stu-id="230e9-413">Ignored.</span></span>|  
|`base`|<span data-ttu-id="230e9-414">Obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="230e9-414">Supported.</span></span> <span data-ttu-id="230e9-415">Typu map do kontraktu danych podstawowych, że ten typ dziedziczy z.</span><span class="sxs-lookup"><span data-stu-id="230e9-415">Maps to the base data contract type that this type inherits from.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="230e9-416">\<xs:Extension > w \<xs:complexContent >: zawartość</span><span class="sxs-lookup"><span data-stu-id="230e9-416">\<xs:extension> in \<xs:complexContent>: contents</span></span>  
 <span data-ttu-id="230e9-417">Reguły są takie same jak w przypadku `<xs:complexType>` zawartość.</span><span class="sxs-lookup"><span data-stu-id="230e9-417">The rules are the same as for `<xs:complexType>` contents.</span></span>  
  
 <span data-ttu-id="230e9-418">Jeśli `<xs:sequence>` podano jego elementów członkowskich elementy mapy do elementów członkowskich dodatkowe dane, które znajdują się w kontraktu danych pochodnych.</span><span class="sxs-lookup"><span data-stu-id="230e9-418">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>  
  
 <span data-ttu-id="230e9-419">Jeśli typ pochodny zawiera element o takiej samej nazwy jak element w typie podstawowym, deklaracji zduplikowany element mapy do elementu członkowskiego danych o nazwie, która jest generowana unikatowa.</span><span class="sxs-lookup"><span data-stu-id="230e9-419">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="230e9-420">Dodatnia liczba całkowita numery są dodawane do nazwę elementu członkowskiego danych ("Członek1", "member2" itd.) aż do znalezienia unikatową nazwę.</span><span class="sxs-lookup"><span data-stu-id="230e9-420">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="230e9-421">Z drugiej strony:</span><span class="sxs-lookup"><span data-stu-id="230e9-421">Conversely:</span></span>  
  
-   <span data-ttu-id="230e9-422">Jeśli kontraktu danych pochodnej ma element członkowski danych z taką samą nazwę i typ jako element członkowski danych w kontrakt danych podstawowych `DataContractSerializer` generuje ten odpowiadający mu element w typie pochodnym.</span><span class="sxs-lookup"><span data-stu-id="230e9-422">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>  
  
-   <span data-ttu-id="230e9-423">Jeśli kontraktu danych pochodnej ma element członkowski danych o takiej samej nazwie jako element członkowski danych, ale jest innego typu kontraktu danych podstawowych `DataContractSerializer` Importuje schemat z elementem typu `xs:anyType` w typie podstawowym i deklaracje typu pochodnego.</span><span class="sxs-lookup"><span data-stu-id="230e9-423">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="230e9-424">Oryginalna nazwa typu jest zachowywana w `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span><span class="sxs-lookup"><span data-stu-id="230e9-424">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>  
  
 <span data-ttu-id="230e9-425">Zarówno zmian może doprowadzić do schematu z niejednoznaczne modelu zawartości, który jest zależny rzędu elementy członkowskie odpowiednich danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-425">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>  
  
## <a name="typeprimitive-mapping"></a><span data-ttu-id="230e9-426">Mapowanie typu/pierwotnego</span><span class="sxs-lookup"><span data-stu-id="230e9-426">Type/primitive mapping</span></span>  
 <span data-ttu-id="230e9-427">`DataContractSerializer` Używa następującego mapowania dla typów pierwotnych schematu XML.</span><span class="sxs-lookup"><span data-stu-id="230e9-427">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>  
  
|<span data-ttu-id="230e9-428">Typ XSD</span><span class="sxs-lookup"><span data-stu-id="230e9-428">XSD type</span></span>|<span data-ttu-id="230e9-429">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="230e9-429">.NET type</span></span>|  
|--------------|---------------|  
|`anyType`|<span data-ttu-id="230e9-430"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="230e9-430"><xref:System.Object>.</span></span>|  
|`anySimpleType`|<span data-ttu-id="230e9-431"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-431"><xref:System.String>.</span></span>|  
|`duration`|<span data-ttu-id="230e9-432"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="230e9-432"><xref:System.TimeSpan>.</span></span>|  
|`dateTime`|<span data-ttu-id="230e9-433"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="230e9-433"><xref:System.DateTime>.</span></span>|  
|`dateTimeOffset`|<span data-ttu-id="230e9-434"><xref:System.DateTime>i <xref:System.TimeSpan> przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="230e9-434"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="230e9-435">Zobacz poniższe serializacji typu DateTimeOffset.</span><span class="sxs-lookup"><span data-stu-id="230e9-435">See DateTimeOffset Serialization below.</span></span>|  
|`time`|<span data-ttu-id="230e9-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-436"><xref:System.String>.</span></span>|  
|`date`|<span data-ttu-id="230e9-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-437"><xref:System.String>.</span></span>|  
|`gYearMonth`|<span data-ttu-id="230e9-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-438"><xref:System.String>.</span></span>|  
|`gYear`|<span data-ttu-id="230e9-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-439"><xref:System.String>.</span></span>|  
|`gMonthDay`|<span data-ttu-id="230e9-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-440"><xref:System.String>.</span></span>|  
|`gDay`|<span data-ttu-id="230e9-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-441"><xref:System.String>.</span></span>|  
|`gMonth`|<span data-ttu-id="230e9-442"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-442"><xref:System.String>.</span></span>|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<span data-ttu-id="230e9-443"><xref:System.Byte>Tablica.</span><span class="sxs-lookup"><span data-stu-id="230e9-443"><xref:System.Byte> array.</span></span>|  
|`hexBinary`|<span data-ttu-id="230e9-444"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-444"><xref:System.String>.</span></span>|  
|`float`|<span data-ttu-id="230e9-445"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="230e9-445"><xref:System.Single>.</span></span>|  
|`double`|<span data-ttu-id="230e9-446"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="230e9-446"><xref:System.Double>.</span></span>|  
|`anyURI`|<span data-ttu-id="230e9-447"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="230e9-447"><xref:System.Uri>.</span></span>|  
|`QName`|<span data-ttu-id="230e9-448"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="230e9-448"><xref:System.Xml.XmlQualifiedName>.</span></span>|  
|`string`|<span data-ttu-id="230e9-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-449"><xref:System.String>.</span></span>|  
|`normalizedString`|<span data-ttu-id="230e9-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-450"><xref:System.String>.</span></span>|  
|`token`|<span data-ttu-id="230e9-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-451"><xref:System.String>.</span></span>|  
|`language`|<span data-ttu-id="230e9-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-452"><xref:System.String>.</span></span>|  
|`Name`|<span data-ttu-id="230e9-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-453"><xref:System.String>.</span></span>|  
|`NCName`|<span data-ttu-id="230e9-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-454"><xref:System.String>.</span></span>|  
|`ID`|<span data-ttu-id="230e9-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-455"><xref:System.String>.</span></span>|  
|`IDREF`|<span data-ttu-id="230e9-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-456"><xref:System.String>.</span></span>|  
|`IDREFS`|<span data-ttu-id="230e9-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-457"><xref:System.String>.</span></span>|  
|`ENTITY`|<span data-ttu-id="230e9-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-458"><xref:System.String>.</span></span>|  
|`ENTITIES`|<span data-ttu-id="230e9-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-459"><xref:System.String>.</span></span>|  
|`NMTOKEN`|<span data-ttu-id="230e9-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-460"><xref:System.String>.</span></span>|  
|`NMTOKENS`|<span data-ttu-id="230e9-461"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="230e9-461"><xref:System.String>.</span></span>|  
|`decimal`|<span data-ttu-id="230e9-462"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="230e9-462"><xref:System.Decimal>.</span></span>|  
|`integer`|<span data-ttu-id="230e9-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="230e9-463"><xref:System.Int64>.</span></span>|  
|`nonPositiveInteger`|<span data-ttu-id="230e9-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="230e9-464"><xref:System.Int64>.</span></span>|  
|`negativeInteger`|<span data-ttu-id="230e9-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="230e9-465"><xref:System.Int64>.</span></span>|  
|`long`|<span data-ttu-id="230e9-466"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="230e9-466"><xref:System.Int64>.</span></span>|  
|`int`|<span data-ttu-id="230e9-467"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="230e9-467"><xref:System.Int32>.</span></span>|  
|`short`|<span data-ttu-id="230e9-468"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="230e9-468"><xref:System.Int16>.</span></span>|  
|`Byte`|<span data-ttu-id="230e9-469"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="230e9-469"><xref:System.SByte>.</span></span>|  
|`nonNegativeInteger`|<span data-ttu-id="230e9-470"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="230e9-470"><xref:System.Int64>.</span></span>|  
|`unsignedLong`|<span data-ttu-id="230e9-471"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="230e9-471"><xref:System.UInt64>.</span></span>|  
|`unsignedInt`|<span data-ttu-id="230e9-472"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="230e9-472"><xref:System.UInt32>.</span></span>|  
|`unsignedShort`|<span data-ttu-id="230e9-473"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="230e9-473"><xref:System.UInt16>.</span></span>|  
|`unsignedByte`|<span data-ttu-id="230e9-474"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="230e9-474"><xref:System.Byte>.</span></span>|  
|`positiveInteger`|<span data-ttu-id="230e9-475"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="230e9-475"><xref:System.Int64>.</span></span>|  
  
## <a name="iserializable-types-mapping"></a><span data-ttu-id="230e9-476">Mapowanie typów iSerializable</span><span class="sxs-lookup"><span data-stu-id="230e9-476">ISerializable types mapping</span></span>  
 <span data-ttu-id="230e9-477">W [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] w wersji 1.0 `ISerializable` została wprowadzona jako mechanizm ogólne do serializacji obiektów do transferu danych lub trwałości.</span><span class="sxs-lookup"><span data-stu-id="230e9-477">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, `ISerializable` was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="230e9-478">Istnieje wiele [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, które implementują `ISerializable` i mogą być przekazywane między aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="230e9-478">There are many [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="230e9-479">`DataContractSerializer`Oczywiście zapewnia obsługę `ISerializable` klasy.</span><span class="sxs-lookup"><span data-stu-id="230e9-479">`DataContractSerializer` naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="230e9-480">`DataContractSerializer` Mapy `ISerializable` implementacja schematu typy, które różnią się tylko wielkością QName (kwalifikowana nazwa) tego typu i są efektywne kolekcji właściwości.</span><span class="sxs-lookup"><span data-stu-id="230e9-480">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="230e9-481">Na przykład `DataContractSerializer` mapuje <xref:System.Exception> do następującego typu XSD w przestrzeni nazw http://schemas.datacontract.org/2004/07/System.</span><span class="sxs-lookup"><span data-stu-id="230e9-481">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the http://schemas.datacontract.org/2004/07/System namespace.</span></span>  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 <span data-ttu-id="230e9-482">Opcjonalny atrybut `ser:FactoryType` zadeklarowany w danych serializacji kontraktu schematu odwołuje się do klasy fabryki, która może wykonywać deserializację typu.</span><span class="sxs-lookup"><span data-stu-id="230e9-482">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="230e9-483">Klasa fabryki muszą być częścią kolekcji znanych typów `DataContractSerializer` wystąpienie używane.</span><span class="sxs-lookup"><span data-stu-id="230e9-483">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="230e9-484">znane typy, zobacz [znane typy kontraktu danych](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span><span class="sxs-lookup"><span data-stu-id="230e9-484"> known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="datacontract-serialization-schema"></a><span data-ttu-id="230e9-485">Schematu serializacji DataContract</span><span class="sxs-lookup"><span data-stu-id="230e9-485">DataContract Serialization Schema</span></span>  
 <span data-ttu-id="230e9-486">Liczba schematów wyeksportowane przez `DataContractSerializer` użyć typów, elementy i atrybuty z specjalne nazw serializacji kontraktu danych:</span><span class="sxs-lookup"><span data-stu-id="230e9-486">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>  
  
 <span data-ttu-id="230e9-487">http://schemas.microsoft.com/2003/10/serialization</span><span class="sxs-lookup"><span data-stu-id="230e9-487">http://schemas.microsoft.com/2003/10/Serialization</span></span>  
  
 <span data-ttu-id="230e9-488">Poniżej znajduje się pełna deklaracja schematu serializacji kontraktu danych.</span><span class="sxs-lookup"><span data-stu-id="230e9-488">The following is a complete Data Contract Serialization schema declaration.</span></span>  
  
```xml  
<xs:schema attributeFormDefault="qualified"          
   elementFormDefault="qualified"        
   targetNamespace =   
    "http://schemas.microsoft.com/2003/10/Serialization/"   
   xmlns:xs="http://www.w3.org/2001/XMLSchema"        
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">  
  
 <!-- Top-level elements for primitive types. -->  
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>  
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>  
 <xs:element name="base64Binary"  
       nillable="true" type="xs:base64Binary"/>  
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>  
 <xs:element name="byte" nillable="true" type="xs:byte"/>  
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>  
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>  
 <xs:element name="double" nillable="true" type="xs:double"/>  
 <xs:element name="float" nillable="true" type="xs:float"/>  
 <xs:element name="int" nillable="true" type="xs:int"/>  
 <xs:element name="long" nillable="true" type="xs:long"/>  
 <xs:element name="QName" nillable="true" type="xs:QName"/>  
 <xs:element name="short" nillable="true" type="xs:short"/>  
 <xs:element name="string" nillable="true" type="xs:string"/>  
 <xs:element name="unsignedByte"  
       nillable="true" type="xs:unsignedByte"/>  
 <xs:element name="unsignedInt"  
       nillable="true" type="xs:unsignedInt"/>  
 <xs:element name="unsignedLong"  
       nillable="true" type="xs:unsignedLong"/>  
 <xs:element name="unsignedShort"  
       nillable="true" type="xs:unsignedShort"/>  
  
 <!-- Primitive types introduced for certain .NET simple types. -->  
 <xs:element name="char" nillable="true" type="tns:char"/>  
 <xs:simpleType name="char">  
  <xs:restriction base="xs:int"/>  
 </xs:simpleType>  
  
 <!-- xs:duration is restricted to an ordered value space,  
    to map to System.TimeSpan -->  
 <xs:element name="duration" nillable="true" type="tns:duration"/>  
 <xs:simpleType name="duration">  
  <xs:restriction base="xs:duration">  
   <xs:pattern   
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>  
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>  
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <xs:element name="guid" nillable="true" type="tns:guid"/>  
 <xs:simpleType name="guid">  
  <xs:restriction base="xs:string">  
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <!-- This is used for schemas exported from ISerializable type. -->  
 <xs:attribute name="FactoryType" type="xs:QName"/>  
</xs:schema>  
```  
  
 <span data-ttu-id="230e9-489">Należy można zauważyć następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="230e9-489">The following should be noted:</span></span>  
  
-   <span data-ttu-id="230e9-490">`ser:char`wprowadzane do reprezentowania znaków Unicode typu <xref:System.Char>.</span><span class="sxs-lookup"><span data-stu-id="230e9-490">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>  
  
-   <span data-ttu-id="230e9-491">`valuespace` z `xs:duration` zostanie zmniejszona do zestawu uporządkowanych, dzięki czemu mogą być mapowane na <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="230e9-491">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>  
  
-   <span data-ttu-id="230e9-492">`FactoryType`jest używany w schematach wyeksportowane z typów, które są pochodnymi <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="230e9-492">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="230e9-493">Importowanie schematów innych niż typ</span><span class="sxs-lookup"><span data-stu-id="230e9-493">Importing non-DataContract schemas</span></span>  
 <span data-ttu-id="230e9-494">`DataContractSerializer`ma `ImportXmlTypes` opcję, aby umożliwić Importowanie schematów, które nie są zgodne z `DataContractSerializer` profilu XSD (zobacz <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> właściwości).</span><span class="sxs-lookup"><span data-stu-id="230e9-494">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="230e9-495">Ustawienie tej opcji na `true` umożliwia akceptacji niezgodnych typów schematów i mapując je do wykonania następujących <xref:System.Xml.Serialization.IXmlSerializable> zawijania tablicę <xref:System.Xml.XmlNode> (różni się tylko nazwę klasy).</span><span class="sxs-lookup"><span data-stu-id="230e9-495">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>  
  
```  
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]  
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]  
public partial class Person : object, IXmlSerializable  
{    
  private XmlNode[] nodesField;    
  private static XmlQualifiedName typeName =   
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");    
  public XmlNode[] Nodes  
  {  
    get {return this.nodesField;}  
    set {this.nodesField = value;}  
  }    
  public void ReadXml(XmlReader reader)  
  {  
    this.nodesField = XmlSerializableServices.ReadNodes(reader);  
  }    
  public void WriteXml(XmlWriter writer)  
  {  
    XmlSerializableServices.WriteNodes(writer, this.Nodes);  
  }    
  public System.Xml.Schema.XmlSchema GetSchema()  
  {  
    return null;  
  }    
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)  
  {  
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);  
    return typeName;  
  }  
}  
```  
  
## <a name="datetimeoffset-serialization"></a><span data-ttu-id="230e9-496">Serializacja DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="230e9-496">DateTimeOffset Serialization</span></span>  
 <span data-ttu-id="230e9-497"><xref:System.DateTimeOffset> Nie jest traktowana jako typ pierwotny.</span><span class="sxs-lookup"><span data-stu-id="230e9-497">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="230e9-498">Zamiast tego jest serializowany jako element złożonych z dwóch części.</span><span class="sxs-lookup"><span data-stu-id="230e9-498">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="230e9-499">Pierwsza część reprezentuje daty, godziny, a druga część — przesunięcie od chwili daty.</span><span class="sxs-lookup"><span data-stu-id="230e9-499">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="230e9-500">Przykład serializacji wartości DateTimeOffset przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="230e9-500">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>  
  
```xml  
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">  
  <DateTime i:type="b:dateTime" xmlns=""   
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00    
  </DateTime>   
  <OffsetMinutes i:type="b:short" xmlns=""   
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480  
   </OffsetMinutes>   
</OffSet>  
```  
  
 <span data-ttu-id="230e9-501">Schemat jest w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="230e9-501">The schema is as follows.</span></span>  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="230e9-502">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="230e9-502">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [<span data-ttu-id="230e9-503">Używanie kontraktów danych</span><span class="sxs-lookup"><span data-stu-id="230e9-503">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
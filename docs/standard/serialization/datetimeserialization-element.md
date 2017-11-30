---
title: "&lt;dateTimeSerialization&gt; — Element"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f925e9e05ab0e9452d81d7a26d33f11506870034
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltdatetimeserializationgt-element"></a><span data-ttu-id="1717e-102">&lt;dateTimeSerialization&gt; — Element</span><span class="sxs-lookup"><span data-stu-id="1717e-102">&lt;dateTimeSerialization&gt; Element</span></span>
<span data-ttu-id="1717e-103">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="1717e-103">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>  
  
 <span data-ttu-id="1717e-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="1717e-104">\<configuration></span></span>  
<span data-ttu-id="1717e-105">\<dateTimeSerialization ></span><span class="sxs-lookup"><span data-stu-id="1717e-105">\<dateTimeSerialization></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1717e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="1717e-106">Syntax</span></span>  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip" | "Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1717e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1717e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1717e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1717e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1717e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1717e-109">Attributes</span></span>  
  
|<span data-ttu-id="1717e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1717e-110">Attributes</span></span>|<span data-ttu-id="1717e-111">Opis</span><span class="sxs-lookup"><span data-stu-id="1717e-111">Description</span></span>|  
|----------------|-----------------|  
|`mode`|<span data-ttu-id="1717e-112">Parametr opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="1717e-112">Optional.</span></span> <span data-ttu-id="1717e-113">Określa tryb serializacji.</span><span class="sxs-lookup"><span data-stu-id="1717e-113">Specifies the serialization mode.</span></span> <span data-ttu-id="1717e-114">Jedną z <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> wartości.</span><span class="sxs-lookup"><span data-stu-id="1717e-114">Set to one of the <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> values.</span></span> <span data-ttu-id="1717e-115">Wartość domyślna to **obie strony**.</span><span class="sxs-lookup"><span data-stu-id="1717e-115">The default is **RoundTrip**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1717e-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1717e-116">Child Elements</span></span>  
 <span data-ttu-id="1717e-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="1717e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1717e-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1717e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1717e-119">Element</span><span class="sxs-lookup"><span data-stu-id="1717e-119">Element</span></span>|<span data-ttu-id="1717e-120">Opis</span><span class="sxs-lookup"><span data-stu-id="1717e-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1717e-121">System.XML.serialization</span><span class="sxs-lookup"><span data-stu-id="1717e-121">system.xml.serialization</span></span>|<span data-ttu-id="1717e-122">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="1717e-122">The top-level element for controlling XML serialization.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1717e-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1717e-123">Remarks</span></span>  
 <span data-ttu-id="1717e-124">W wersjach 1.0, 1.1, 2.0 i nowsze wersje programu .NET Framework, gdy ta właściwość jest ustawiona na **lokalnego**, <xref:System.DateTime> obiekty są zawsze formatowane jako czas lokalny.</span><span class="sxs-lookup"><span data-stu-id="1717e-124">In versions 1.0, 1.1, 2.0 and later versions of the .NET Framework, when this property is set to **Local**, <xref:System.DateTime> objects are always formatted as the local time.</span></span> <span data-ttu-id="1717e-125">Oznacza to, że informacje o strefie czas lokalny zawsze jest zawarte w danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="1717e-125">That is, local time zone information is always included with the serialized data.</span></span> <span data-ttu-id="1717e-126">Ta właściwość jest ustawiana **lokalnego** aby zapewnić zgodność ze starszymi wersjami programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1717e-126">Set this property to **Local** to ensure compatibility with older versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1717e-127">W wersji 2.0 i nowszych wersji programu .NET Framework, które ta właściwość ma wartość **obie strony**, <xref:System.DateTime> obiekty są sprawdzane w celu ustalenia, czy są w lokalnym, UTC lub nieokreślona strefy czasowej.</span><span class="sxs-lookup"><span data-stu-id="1717e-127">In version 2.0 and later versions of the .NET Framework that have this property set to **Roundtrip**, <xref:System.DateTime> objects are examined to determine whether they are in the local, UTC, or an unspecified time zone.</span></span> <span data-ttu-id="1717e-128"><xref:System.DateTime> Obiekty są następnie serializowany w taki sposób, że jest zachowywany tych informacji.</span><span class="sxs-lookup"><span data-stu-id="1717e-128">The <xref:System.DateTime> objects are then serialized in such a way that this information is preserved.</span></span> <span data-ttu-id="1717e-129">Jest to domyślne zachowanie, zalecane zachowanie dla wszystkich nowych aplikacji, które nie komunikują się ze starszymi wersjami platformy.</span><span class="sxs-lookup"><span data-stu-id="1717e-129">This is the default behavior and is the recommended behavior for all new applications that do not communicate with older versions of the framework.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1717e-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1717e-130">See Also</span></span>  
 <xref:System.DateTime>  
 <xref:System.Xml.Serialization.XmlSchemaImporter>  
 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>  
 [<span data-ttu-id="1717e-131">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1717e-131">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="1717e-132">\<schemaImporterExtensions > — Element</span><span class="sxs-lookup"><span data-stu-id="1717e-132">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 [<span data-ttu-id="1717e-133">\<Dodaj > elementu \<xmlSchemaImporterExtensions ></span><span class="sxs-lookup"><span data-stu-id="1717e-133">\<add> Element for \<xmlSchemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 [<span data-ttu-id="1717e-134">\<System.XML.serialization > — Element</span><span class="sxs-lookup"><span data-stu-id="1717e-134">\<system.xml.serialization> Element</span></span>](../../../docs/standard/serialization/system-xml-serialization-element.md)
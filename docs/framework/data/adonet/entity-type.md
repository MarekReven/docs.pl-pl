---
title: Typ jednostki
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1b84ff5a55cff4548539e81b16406e234dcb43f9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="entity-type"></a><span data-ttu-id="56a82-102">Typ jednostki</span><span class="sxs-lookup"><span data-stu-id="56a82-102">entity type</span></span>
<span data-ttu-id="56a82-103">*Typu jednostki* jest podstawowym blokiem opisu struktury danych z modelu danych jednostki (EDM).</span><span class="sxs-lookup"><span data-stu-id="56a82-103">The *entity type* is the fundamental building block for describing the structure of data with the Entity Data Model (EDM).</span></span> <span data-ttu-id="56a82-104">W modelu koncepcyjnym typem jednostki reprezentuje strukturę pojęcia najwyższego poziomu, takie jak klienci lub zamówienia.</span><span class="sxs-lookup"><span data-stu-id="56a82-104">In a conceptual model, an entity type represents the structure of top-level concepts, such as customers or orders.</span></span> <span data-ttu-id="56a82-105">Typ jednostki jest szablon dla wystąpień typów jednostek.</span><span class="sxs-lookup"><span data-stu-id="56a82-105">An entity type is a template for entity type instances.</span></span> <span data-ttu-id="56a82-106">Każdy szablon zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="56a82-106">Each template contains the following information:</span></span>  
  
-   <span data-ttu-id="56a82-107">Unikatowa nazwa.</span><span class="sxs-lookup"><span data-stu-id="56a82-107">A unique name.</span></span> <span data-ttu-id="56a82-108">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="56a82-108">(Required.)</span></span>  
  
-   <span data-ttu-id="56a82-109">[Klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) zdefiniowane przez co najmniej jednej właściwości.</span><span class="sxs-lookup"><span data-stu-id="56a82-109">An [entity key](../../../../docs/framework/data/adonet/entity-key.md) defined by one or more properties.</span></span> <span data-ttu-id="56a82-110">(Wymagane).</span><span class="sxs-lookup"><span data-stu-id="56a82-110">(Required.)</span></span>  
  
-   <span data-ttu-id="56a82-111">Dane w postaci [właściwości](../../../../docs/framework/data/adonet/property.md).</span><span class="sxs-lookup"><span data-stu-id="56a82-111">Data in the form of [properties](../../../../docs/framework/data/adonet/property.md).</span></span> <span data-ttu-id="56a82-112">(Opcjonalnie).</span><span class="sxs-lookup"><span data-stu-id="56a82-112">(Optional.)</span></span>  
  
-   <span data-ttu-id="56a82-113">[Właściwości nawigacji](../../../../docs/framework/data/adonet/navigation-property.md) umożliwiające nawigacji z jednego [zakończenia](../../../../docs/framework/data/adonet/association-end.md) z [skojarzenia](../../../../docs/framework/data/adonet/association-type.md) w innym celu.</span><span class="sxs-lookup"><span data-stu-id="56a82-113">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) that allow for navigation from one [end](../../../../docs/framework/data/adonet/association-end.md) of an [association](../../../../docs/framework/data/adonet/association-type.md) to the other end.</span></span> <span data-ttu-id="56a82-114">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="56a82-114">(Optional)</span></span>  
  
 <span data-ttu-id="56a82-115">W aplikacji wystąpienia typu jednostki reprezentuje określonego obiektu (na przykład odbiorcę lub kolejność).</span><span class="sxs-lookup"><span data-stu-id="56a82-115">In an application, an instance of an entity type represents a specific object (such as a specific customer or order).</span></span> <span data-ttu-id="56a82-116">Każde wystąpienie typu jednostki musi mieć unikatową [klucz jednostki](../../../../docs/framework/data/adonet/entity-key.md) w [zestaw jednostek](../../../../docs/framework/data/adonet/entity-set.md).</span><span class="sxs-lookup"><span data-stu-id="56a82-116">Each instance of an entity type must have a unique [entity key](../../../../docs/framework/data/adonet/entity-key.md) within an [entity set](../../../../docs/framework/data/adonet/entity-set.md).</span></span>  
  
 <span data-ttu-id="56a82-117">Dwa wystąpienia typu jednostki są traktowane jako równe tylko wtedy, gdy są tego samego typu i wartości kluczy jednostki są takie same.</span><span class="sxs-lookup"><span data-stu-id="56a82-117">Two entity type instances are considered equal only if they are of the same type and the values of their entity keys are the same.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56a82-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="56a82-118">Example</span></span>  
 <span data-ttu-id="56a82-119">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`:</span><span class="sxs-lookup"><span data-stu-id="56a82-119">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`:</span></span>  
  
 <span data-ttu-id="56a82-120">![Przykładowy Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="56a82-120">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="56a82-121">Należy pamiętać, że właściwości poszczególnych typów jednostek, które tworzą kluczem jednostki są oznaczone symbolem "(klucz)".</span><span class="sxs-lookup"><span data-stu-id="56a82-121">Note that the properties of each entity type that make up its entity key are denoted with "(Key)".</span></span>  
  
 <span data-ttu-id="56a82-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="56a82-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="56a82-123">Definiuje następujące CSDL `Book` typu jednostki pokazano na powyższym diagramie:</span><span class="sxs-lookup"><span data-stu-id="56a82-123">The following CSDL defines the `Book` entity type shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="56a82-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56a82-124">See Also</span></span>  
 [<span data-ttu-id="56a82-125">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="56a82-125">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="56a82-126">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="56a82-126">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="56a82-127">aspekt</span><span class="sxs-lookup"><span data-stu-id="56a82-127">facet</span></span>](../../../../docs/framework/data/adonet/facet.md)
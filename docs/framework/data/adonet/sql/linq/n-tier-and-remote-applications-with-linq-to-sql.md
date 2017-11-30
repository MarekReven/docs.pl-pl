---
title: "N-warstwowa oraz zdalnych aplikacji za pomocą LINQ do SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f44b6da8ecc8d036a9550856f71b2981770e9478
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="n-tier-and-remote-applications-with-linq-to-sql"></a><span data-ttu-id="da05f-102">N-warstwowa oraz zdalnych aplikacji za pomocą LINQ do SQL</span><span class="sxs-lookup"><span data-stu-id="da05f-102">N-Tier and Remote Applications with LINQ to SQL</span></span>
<span data-ttu-id="da05f-103">Można utworzyć n warstwowa lub wielowarstwowej aplikacji, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da05f-103">You can create n-tier or multitier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="da05f-104">Zazwyczaj [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kontekstu danych, klas jednostek i logiki konstrukcji zapytania znajdują się na warstwę środkową jako warstwa dostępu do danych (DAL).</span><span class="sxs-lookup"><span data-stu-id="da05f-104">Typically, the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] data context, entity classes, and query construction logic are located on the middle tier as the data access layer (DAL).</span></span> <span data-ttu-id="da05f-105">Logika biznesowa i trwałe dane może być całkowicie wdrożonych w klasy częściowe i metody jednostki oraz kontekst danych lub można ją wdrożyć w osobnych klas.</span><span class="sxs-lookup"><span data-stu-id="da05f-105">Business logic and any non-persistent data can be implemented completely in partial classes and methods of entities and the data context, or it can be implemented in separate classes.</span></span>  
  
 <span data-ttu-id="da05f-106">Warstwa prezentacji lub klienta wywołuje metody interfejsu zdalnego warstwy środkowej i warstwy DAL w tej warstwie wykona zapytania lub procedur składowanych, które są mapowane na <xref:System.Data.Linq.DataContext> metody.</span><span class="sxs-lookup"><span data-stu-id="da05f-106">The client or presentation layer calls methods on the middle-tier's remote interface, and the DAL on that tier will execute queries or stored procedures that are mapped to <xref:System.Data.Linq.DataContext> methods.</span></span> <span data-ttu-id="da05f-107">Warstwy środkowej zwraca dane do klientów zwykle jako jednostek lub obiektów pośredniczących reprezentacji XML.</span><span class="sxs-lookup"><span data-stu-id="da05f-107">The middle tier returns the data to clients typically as XML representations of entities or proxy objects.</span></span>  
  
 <span data-ttu-id="da05f-108">W warstwie środkowej jednostki są tworzone przez kontekst danych, który śledzi ich stan i zarządza ładowanie odłożone z i przesłanie zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="da05f-108">On the middle tier, entities are created by the data context, which tracks their state, and manages deferred loading from and submission of changes to the database.</span></span> <span data-ttu-id="da05f-109">Te jednostki "dołączonych" do `DataContext`.</span><span class="sxs-lookup"><span data-stu-id="da05f-109">These entities are "attached" to the `DataContext`.</span></span> <span data-ttu-id="da05f-110">Jednak po jednostek są wysyłane do innej warstwy za pomocą serializacji, stają się one odłączony, co oznacza, że `DataContext` już służy do śledzenia stanu.</span><span class="sxs-lookup"><span data-stu-id="da05f-110">However, after the entities are sent to another tier through serialization, they become detached, which means the `DataContext` is no longer tracking their state.</span></span> <span data-ttu-id="da05f-111">Jednostki, które klient wysyła ponownie dla aktualizacji musi zostać ponownie nałożona kontekst danych przed [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] można przesłać zmian w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="da05f-111">Entities that the client sends back for updates must be reattached to the data context before [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] can submit the changes to the database.</span></span> <span data-ttu-id="da05f-112">Klient jest odpowiedzialny za zapewnienie oryginalnych wartości i/lub sygnatury czasowe z powrotem do warstwy środkowej, jeśli są wymagane dla sprawdzenie optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="da05f-112">The client is responsible for providing original values and/or timestamps back to the middle tier if those are required for optimistic concurrency checks.</span></span>  
  
 <span data-ttu-id="da05f-113">W aplikacjach ASP.NET <xref:System.Web.UI.WebControls.LinqDataSource> zarządza większość tego złożoności.</span><span class="sxs-lookup"><span data-stu-id="da05f-113">In ASP.NET applications, the <xref:System.Web.UI.WebControls.LinqDataSource> manages most of this complexity.</span></span> <span data-ttu-id="da05f-114">Aby uzyskać więcej informacji, zobacz [NIB: omówienie kontrolki serwera sieci Web LinqDataSource](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span><span class="sxs-lookup"><span data-stu-id="da05f-114">For more information, see [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/en-us/104cfc3f-7385-47d3-8a51-830dfa791136).</span></span>  
  
## <a name="additional-resources"></a><span data-ttu-id="da05f-115">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="da05f-115">Additional Resources</span></span>  
 <span data-ttu-id="da05f-116">Aby uzyskać więcej informacji na temat sposobu wdrażania aplikacje warstwowe, które używają [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], zobacz następujące tematy:</span><span class="sxs-lookup"><span data-stu-id="da05f-116">For more information about how to implement n-tier applications that use [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], see the following topics:</span></span>  
  
-   [<span data-ttu-id="da05f-117">LINQ do SQL N-warstwowa ASP.NET</span><span class="sxs-lookup"><span data-stu-id="da05f-117">LINQ to SQL N-Tier with ASP.NET</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [<span data-ttu-id="da05f-118">LINQ do SQL N-warstwowa z usługami sieci Web</span><span class="sxs-lookup"><span data-stu-id="da05f-118">LINQ to SQL N-Tier with Web Services</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [<span data-ttu-id="da05f-119">LINQ do SQL z aplikacjami ściśle powiązane klient serwer</span><span class="sxs-lookup"><span data-stu-id="da05f-119">LINQ to SQL with Tightly-Coupled Client-Server Applications</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [<span data-ttu-id="da05f-120">Implementowanie logiki biznesowej N-warstwowa</span><span class="sxs-lookup"><span data-stu-id="da05f-120">Implementing N-Tier Business Logic</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [<span data-ttu-id="da05f-121">Pobieranie danych i CUD operacje w aplikacjach warstwowych (LINQ to SQL)</span><span class="sxs-lookup"><span data-stu-id="da05f-121">Data Retrieval and CUD Operations in N-Tier Applications (LINQ to SQL)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 <span data-ttu-id="da05f-122">Aby uzyskać więcej informacji o aplikacjach warstwowych, które używają danych ADO.NET, zobacz [Praca z zestawami danych w aplikacjach warstwowych](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span><span class="sxs-lookup"><span data-stu-id="da05f-122">For more information about n-tier applications that use ADO.NET DataSets, see [Work with datasets in n-tier applications](http://msdn.microsoft.com/library/f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da05f-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da05f-123">See Also</span></span>  
 [<span data-ttu-id="da05f-124">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="da05f-124">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
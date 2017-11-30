---
title: "Porady: Dodawanie odwołania do danych usługi (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a8fb075bdb17f0d562d752bc4125141bb0bb2ab9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="d1186-102">Porady: Dodawanie odwołania do danych usługi (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="d1186-102">How to: Add a Data Service Reference (WCF Data Services)</span></span>
<span data-ttu-id="d1186-103">Można użyć **Dodaj odwołanie do usługi** okna dialogowego w programie Visual Studio można dodać odwołania do [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d1186-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="d1186-104">Dzięki temu można łatwiej dostępu do usługi danych w aplikacji klienckiej, która opracowywania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d1186-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="d1186-105">Po zakończeniu tej procedury, klas danych są generowane na podstawie metadanych, które są uzyskiwane z usługi data.</span><span class="sxs-lookup"><span data-stu-id="d1186-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="d1186-106">Aby uzyskać więcej informacji, zobacz [generowania biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d1186-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>  
  
### <a name="to-add-a-data-service-reference"></a><span data-ttu-id="d1186-107">Aby dodać odwołania do usługi danych</span><span class="sxs-lookup"><span data-stu-id="d1186-107">To add a data service reference</span></span>  
  
1.  <span data-ttu-id="d1186-108">(Opcjonalnie) Jeśli usługa danych nie jest częścią rozwiązania i nie jest już uruchomiona, uruchom usługę danych i Zanotuj identyfikator URI usługi danych.</span><span class="sxs-lookup"><span data-stu-id="d1186-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>  
  
2.  <span data-ttu-id="d1186-109">Kliknij prawym przyciskiem myszy projekt klienta, a następnie wybierz **Dodaj odwołanie do usługi**.</span><span class="sxs-lookup"><span data-stu-id="d1186-109">Right-click the client project and then select **Add Service Reference**.</span></span>  
  
3.  <span data-ttu-id="d1186-110">Usługi danych jest częścią bieżącego rozwiązania, kliknij przycisk **odnajdowania**.</span><span class="sxs-lookup"><span data-stu-id="d1186-110">If the data service is part of the current solution, click **Discover**.</span></span>  
  
     <span data-ttu-id="d1186-111">—lub—</span><span class="sxs-lookup"><span data-stu-id="d1186-111">-or-</span></span>  
  
     <span data-ttu-id="d1186-112">W **adres** polu tekstowym, wpisz podstawowy adres URL usługi danych, takich jak `http://localhost:1234/Northwind.svc`, a następnie kliknij przycisk **Przejdź**.</span><span class="sxs-lookup"><span data-stu-id="d1186-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>  
  
4.  <span data-ttu-id="d1186-113">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d1186-113">Click **OK**.</span></span>  
  
     <span data-ttu-id="d1186-114">Spowoduje to dodanie nowego pliku kodu zawierającego klas danych, które są używane do uzyskania dostępu i interakcji z zasobami usługi danych jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="d1186-114">This adds a new code file that contains the data classes that are used to access and interact with data service resources as objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1186-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1186-115">See Also</span></span>  
 [<span data-ttu-id="d1186-116">Szybki Start</span><span class="sxs-lookup"><span data-stu-id="d1186-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
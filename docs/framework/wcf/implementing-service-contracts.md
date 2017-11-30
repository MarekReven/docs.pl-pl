---
title: "Implementowanie kontraktów usług"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b40b93b33e57bf15b7ab614405ccffa44abb8df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-service-contracts"></a><span data-ttu-id="0b98a-102">Implementowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="0b98a-102">Implementing Service Contracts</span></span>
<span data-ttu-id="0b98a-103">Usługa jest klasa, która udostępnia funkcje dostępne dla klientów na jeden lub więcej punktów końcowych.</span><span class="sxs-lookup"><span data-stu-id="0b98a-103">A service is a class that exposes functionality available to clients at one or more endpoints.</span></span> <span data-ttu-id="0b98a-104">Aby utworzyć usługę, należy zapisać klasy, która implementuje [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b98a-104">To create a service, write a class that implements a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] contract.</span></span> <span data-ttu-id="0b98a-105">Można w tym na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="0b98a-105">You can do this in one of two ways.</span></span> <span data-ttu-id="0b98a-106">Można zdefiniować kontrakt oddzielnie jako interfejs, a następnie utworzyć klasę, która implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="0b98a-106">You can define the contract separately as an interface and then create a class that implements that interface.</span></span> <span data-ttu-id="0b98a-107">Alternatywnie można utworzyć klasy i kontraktu bezpośrednio przez umieszczenie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu w samej klasy i <xref:System.ServiceModel.OperationContractAttribute> atrybutu w metodach dostępne dla klientów usługi.</span><span class="sxs-lookup"><span data-stu-id="0b98a-107">Alternatively, you can create the class and contract directly by placing the <xref:System.ServiceModel.ServiceContractAttribute> attribute on the class itself and the <xref:System.ServiceModel.OperationContractAttribute> attribute on the methods available to the clients of the service.</span></span>  
  
## <a name="creating-a-service-class"></a><span data-ttu-id="0b98a-108">Tworzenie klasy usługi</span><span class="sxs-lookup"><span data-stu-id="0b98a-108">Creating a service class</span></span>  
 <span data-ttu-id="0b98a-109">Poniżej przedstawiono przykład usługa, która implementuje `IMath` kontraktu, który został zdefiniowany oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="0b98a-109">The following is an example of a service that implements an `IMath` contract that has been defined separately.</span></span>  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="0b98a-110">Alternatywnie usługa może bezpośrednio ujawnianie kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b98a-110">Alternatively, a service can expose a contract directly.</span></span> <span data-ttu-id="0b98a-111">Poniżej przedstawiono przykład klasy usługi, która określa i wykonuje `MathService` kontraktu.</span><span class="sxs-lookup"><span data-stu-id="0b98a-111">The following is an example of a service class that defines and implements a `MathService` contract.</span></span>  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 <span data-ttu-id="0b98a-112">Należy pamiętać, poprzedniego usług ujawnić różne kontrakty, ponieważ nazwy kontraktu różnią się.</span><span class="sxs-lookup"><span data-stu-id="0b98a-112">Note that the preceding services expose different contracts because the contract names are different.</span></span> <span data-ttu-id="0b98a-113">W pierwszym przypadku narażonych kontraktu o nazwie "`IMath`"podczas w drugim przypadku nosi nazwę kontraktu"`MathService`".</span><span class="sxs-lookup"><span data-stu-id="0b98a-113">In the first case, the exposed contract is named "`IMath`" while in the second case the contract is named "`MathService`".</span></span>  
  
 <span data-ttu-id="0b98a-114">Kilka rzeczy można ustawić na usługi i operacji poziomy wdrożenia, takich jak współbieżności i wystąpień.</span><span class="sxs-lookup"><span data-stu-id="0b98a-114">You can set a few things at the service and operation implementation levels, such as concurrency and instancing.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="0b98a-115">[Projektowanie i Implementowanie usług](../../../docs/framework/wcf/designing-and-implementing-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b98a-115"> [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md).</span></span>  
  
 <span data-ttu-id="0b98a-116">Po wdrożeniu kontraktu usługi, należy utworzyć jeden lub więcej punktów końcowych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="0b98a-116">After implementing a service contract, you must create one or more endpoints for the service.</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="0b98a-117">[Przegląd tworzenia punktów końcowych](../../../docs/framework/wcf/endpoint-creation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0b98a-117"> [Endpoint Creation Overview](../../../docs/framework/wcf/endpoint-creation-overview.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="0b98a-118">Uruchamianie usługi, zobacz [Hosting usług](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="0b98a-118"> how to run a service, see [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b98a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0b98a-119">See Also</span></span>  
 [<span data-ttu-id="0b98a-120">Projektowanie i Implementowanie usług</span><span class="sxs-lookup"><span data-stu-id="0b98a-120">Designing and Implementing Services</span></span>](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [<span data-ttu-id="0b98a-121">Porady: Tworzenie usługi za pomocą klasy kontraktu</span><span class="sxs-lookup"><span data-stu-id="0b98a-121">How to: Create a Service with a Contract Class</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [<span data-ttu-id="0b98a-122">Porady: Tworzenie usługi przy użyciu interfejsu kontraktu</span><span class="sxs-lookup"><span data-stu-id="0b98a-122">How to: Create a Service with a Contract Interface</span></span>](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [<span data-ttu-id="0b98a-123">Określanie zachowania środowiska uruchomieniowego usługi</span><span class="sxs-lookup"><span data-stu-id="0b98a-123">Specifying Service Run-Time Behavior</span></span>](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
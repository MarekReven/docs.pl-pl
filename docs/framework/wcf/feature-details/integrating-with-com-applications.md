---
title: "Współdziałanie z aplikacjami COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a0e625beaf20f6445099d8fb15cb175d3d71a860
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications"></a><span data-ttu-id="3a649-102">Współdziałanie z aplikacjami COM</span><span class="sxs-lookup"><span data-stu-id="3a649-102">Integrating with COM Applications</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3a649-103">usługi można zintegrować bezpośrednio do istniejącego kodu za pomocą [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] krótkiej nazwy.</span><span class="sxs-lookup"><span data-stu-id="3a649-103"> services can be integrated directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="3a649-104">Krótka nazwa usługi może służyć w środowiskach programistycznych szeroki zakres modelu COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="3a649-104">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a649-105">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="3a649-105">In This Section</span></span>  
 [<span data-ttu-id="3a649-106">Przegląd integrowania z COM aplikacjami</span><span class="sxs-lookup"><span data-stu-id="3a649-106">Integrating with COM Applications Overview</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 <span data-ttu-id="3a649-107">Zawiera omówienie głównych części procesu integracji.</span><span class="sxs-lookup"><span data-stu-id="3a649-107">Gives an overview of the major parts of the integration process.</span></span>  
  
 [<span data-ttu-id="3a649-108">Porady: zarejestrować i skonfigurować krótkiej nazwy</span><span class="sxs-lookup"><span data-stu-id="3a649-108">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 <span data-ttu-id="3a649-109">Aby użyć [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] krótką nazwę aplikacji modelu COM, zarejestruj wymagane typy oparte na atrybutach w modelu COM i skonfiguruj aplikacji modelu COM i krótka nazwa za pomocą konfiguracji powiązania wymagany.</span><span class="sxs-lookup"><span data-stu-id="3a649-109">To use the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker within a COM application, register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
 [<span data-ttu-id="3a649-110">Porady: Użyj Moniker usługi Windows Communication Foundation bez rejestracji</span><span class="sxs-lookup"><span data-stu-id="3a649-110">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 <span data-ttu-id="3a649-111">Wyjaśniono, jak uzyskać definicję kontraktu w formie dokumentu sieci Web Services Definition Language (WSDL) lub z punktu końcowego usługi WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="3a649-111">Explains how to obtain the definition of the contract in the form of a Web Services Definition Language (WSDL) document or from a WS-MetadataExchange endpoint.</span></span>  
  
 [<span data-ttu-id="3a649-112">Porady: używanie krótkiej nazwy z kontraktami WSDL</span><span class="sxs-lookup"><span data-stu-id="3a649-112">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 <span data-ttu-id="3a649-113">Opisuje sposób wywoływania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbkowania przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span><span class="sxs-lookup"><span data-stu-id="3a649-113">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] WSDL moniker.</span></span>  
  
 [<span data-ttu-id="3a649-114">Porady: używanie krótkiej nazwy z kontraktami wymiany metadanych</span><span class="sxs-lookup"><span data-stu-id="3a649-114">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 <span data-ttu-id="3a649-115">Opisuje sposób wywoływania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] próbkowania przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] krótkiej nazwy, która określa punkt końcowy Mex.</span><span class="sxs-lookup"><span data-stu-id="3a649-115">Describes how to call a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sample using a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] moniker that specifies a Mex endpoint.</span></span>  
  
 [<span data-ttu-id="3a649-116">Porady: Określ poświadczenia zabezpieczeń kanału</span><span class="sxs-lookup"><span data-stu-id="3a649-116">How to: Specify Channel Security Credentials</span></span>](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 <span data-ttu-id="3a649-117">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Usługi obsługuje moniker `IChannelCredentials` interfejs, umożliwiający szereg alternatywnych metod dotyczących określania poświadczeń kanału.</span><span class="sxs-lookup"><span data-stu-id="3a649-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker supports the `IChannelCredentials` interface that allows a range of alternate methods for specifying channel credentials.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3a649-118">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="3a649-118">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a><span data-ttu-id="3a649-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a649-119">See Also</span></span>  
 [<span data-ttu-id="3a649-120">Współdziałanie z aplikacjami COM +</span><span class="sxs-lookup"><span data-stu-id="3a649-120">Integrating with COM+ Applications</span></span>](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
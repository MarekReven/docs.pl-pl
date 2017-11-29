---
title: '&lt;claimTypeRequirements&gt; w &lt;message&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 747ac641f8602010819baa00033f3663e2e5f678
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a>&lt;claimTypeRequirements&gt; w &lt;message&gt;
Określa kolekcję wymaganych typów oświadczeń.  
  
 Kolekcja jest używana przez usługę do określania wymaganych i opcjonalnych oświadczeń, które muszą być w wystawionego tokenu, którego klient używa do uzyskania dostępu do usługi. Usługa przedstawia wymaganych typów oświadczeń w metadanych, jeśli publikowanie WSDL jest włączona, ale WCF nie wymaga wystawiony token zawiera typy określone oświadczenie. Usługi chcą wymusić typy są obecne wymagane oświadczeń należy wykonać przy użyciu zasad autoryzacji.  
  
 Na klientach federacyjnych Ta kolekcja zawiera listę wymaganych i opcjonalnych oświadczeń, które są przesyłane do usługi tokenu zabezpieczającego w żądaniu klienta dla wystawionego tokenu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
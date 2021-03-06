---
title: "Punkty końcowe: Adresy, powiązania i kontrakty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- endpoints [WCF]
- Windows Communication Foundation [WCF], endpoints
- WCF [WCF], endpoints
ms.assetid: 9ddc46ee-1883-4291-9926-28848c57e858
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af82cb934570b371d332c0e08ebc9b2338d0c0d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="endpoints-addresses-bindings-and-contracts"></a>Punkty końcowe: Adresy, powiązania i kontrakty
Cała komunikacja z [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usługi odbywa się przez *punkty końcowe* usługi. Punkty końcowe zapewnić klientom dostęp do funkcji oferowanych przez [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.  
  
 Każdy punkt końcowy składa się z czterech właściwości:  
  
-   Adres, który wskazuje, gdzie można znaleźć punktu końcowego.  
  
-   Wiązanie, który określa, jak klient może komunikować się z punktem końcowym.  
  
-   Kontrakt określa operacje dostępne.  
  
-   Zestaw zachowań, które określają szczegóły implementacji lokalnego punktu końcowego.  
  
 W tym temacie omówiono tego punktu końcowego struktury oraz wyjaśniono, jak są reprezentowane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obiektu modelu.  
  
## <a name="the-structure-of-an-endpoint"></a>Struktura punktu końcowego  
 Każdy punkt końcowy składa się z następujących czynności:  
  
-   Adres: Adres unikatowo identyfikuje punkt końcowy i informuje potencjalne korzystającym z usług, w którym znajduje się. Jest reprezentowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model obiektów przez <xref:System.ServiceModel.EndpointAddress> klasy. <xref:System.ServiceModel.EndpointAddress> Klasa zawiera:  
  
    -   A <xref:System.ServiceModel.EndpointAddress.Uri%2A> właściwość, która reprezentuje adres usługi.  
  
    -   <xref:System.ServiceModel.EndpointAddress.Identity%2A> Właściwość, która reprezentuje tożsamości zabezpieczeń usługi i kolekcję nagłówków komunikatów opcjonalne. Nagłówki komunikatów opcjonalne służą do zapewniania dodatkowe i bardziej szczegółowych informacji o adresach do identyfikacji użytkownika lub interakcji z punktem końcowym.  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Określanie adresu punktu końcowego](../../../../docs/framework/wcf/specifying-an-endpoint-address.md).  
  
-   Powiązanie: Powiązanie określa sposób komunikowania się z punktem końcowym. Możliwości obejmują:  
  
    -   Protokół transportu do użycia (np. TCP lub HTTP).  
  
    -   Szyfrowanie do użycia dla wiadomości (na przykład tekst lub binarny).  
  
    -   Niezbędne wymagania dotyczące zabezpieczeń (na przykład protokołu SSL lub protokołu SOAP wiadomości zabezpieczeń).  
  
     [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Omówienie powiązań WCF](../../../../docs/framework/wcf/bindings-overview.md). Powiązanie jest reprezentowana w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model obiektów przez abstrakcyjna klasa podstawowa <xref:System.ServiceModel.Channels.Binding>. W przypadku większości scenariuszy użytkownicy mogą używać jednego powiązania dostarczane przez system. Aby uzyskać więcej informacji, zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md).  
  
-   Kontrakty: Kontrakt przedstawiono funkcje punktu końcowego udostępnia do klienta. Kontrakt określa:  
  
    -   Jakie operacje może zostać wywołany przez klienta.  
  
    -   Formularz wiadomości.  
  
    -   Typ parametrów wejściowych lub danych wymaganych do wywołania operacji.  
  
    -   Jakiego typu Przetwarzanie lub odpowiedzi wiadomości przez klienta może spodziewać się.  
  
     Aby uzyskać więcej informacji na temat definiowania kontrakt, zobacz [projektowanie kontraktów usług](../../../../docs/framework/wcf/designing-service-contracts.md).  
  
-   Zachowania: Aby dostosować zachowanie lokalnego punktu końcowego usługi można użyć zachowania punktu końcowego. Zachowania punktu końcowego to zrobić, uczestnictwa w procesie tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]środowiska wykonawczego. Przykład zachowania punktu końcowego <xref:System.ServiceModel.Description.ServiceEndpoint.ListenUri%2A> właściwość, która pozwala na określenie nasłuchiwania inny adres niż adres SOAP lub Web Services Description Language (WSDL). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ClientViaBehavior](../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md).  
  
## <a name="defining-endpoints"></a>Definiowanie punktów końcowych  
 Można określić punktu końcowego usługi za pomocą kodu imperatively lub deklaratywnie przy użyciu konfiguracji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md) i [porady: Tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 W tej sekcji opisano w celu powiązania, punktów końcowych i adresy; Pokazuje, jak skonfigurować powiązania i punktu końcowego; i przedstawiono sposób użycia `ClientVia` zachowania i `ListenUri` właściwości.  
  
 [Adresy](../../../../docs/framework/wcf/feature-details/endpoint-addresses.md)  
 W tym artykule opisano, jak punkty końcowe zostały rozwiązane w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
 Opisuje sposób powiązania są używane do określania transportu, kodowanie i szczegóły protokołu wymagane dla klientów i usług komunikować się ze sobą.  
  
 [Kontrakty](../../../../docs/framework/wcf/feature-details/contracts.md)  
 W tym artykule opisano, jak kontrakty definiować metody usługi.  
  
 [Instrukcje: tworzenie punktu końcowego usługi w konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)  
 Opisuje sposób tworzenia punktu końcowego usługi w konfiguracji.  
  
 [Instrukcje: tworzenie punktu końcowego usługi w kodzie](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-endpoint-in-code.md)  
 Opisuje sposób tworzenia punktu końcowego usługi w kodzie.  
  
 [Instrukcje: weryfikacja skompilowanego kodu usługi za pomocą programu Svcutil.exe](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-validate-compiled-service-code.md)  
 Opisuje sposób wykrywania błędów w implementacji usługi i konfiguracji bez hostingu za pomocą usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usług](../../../../docs/framework/wcf/configuring-services.md)  
 [Rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md)

---
title: "Tworzenie usług WCF w technologii AJAX na platformie ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04c0402c-e617-4ba5-aedf-d17692234776
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c2e3ba1d360c55f10cde9447b3961d84ffe1cdb2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="creating-wcf-services-for-aspnet-ajax"></a>Tworzenie usług WCF w technologii AJAX na platformie ASP.NET
Microsoft ASP.NET AJAX umożliwia szybkie tworzenie strony sieci Web, które zawierają użyciu zaawansowanego środowiska użytkownika z elementów interfejsu użytkownika dynamiczne i znanych. ASP.NET AJAX udostępnia biblioteki skryptu klienta, które wyposażone w różnych przeglądarkach ECMAScript (JavaScript) i dynamiczna technologii HTML (DHTML), a on zintegrowany z platformą ASP.NET 2.0 Programowanie oparte na serwerze. Za pomocą kodu ASP.NET AJAX, można ulepszyć środowisko użytkownika i wydajności aplikacji sieci Web.  
  
 ASP.NET AJAX składa się biblioteki klienta skryptów i składniki serwera, które są zintegrowane pod kątem udostępnienia struktury Programowanie niezawodnych. Do uzyskania dostępu do usługi ze strony programu ASP.NET: po dodaniu adres URL usługi do kontrolki Menedżera skryptów platformy ASP.NET na stronie operacji usługi może być wywoływane przy użyciu kodu JavaScript, która wygląda tak samo jak regularne wywołanie funkcji JavaScript. Zobacz [Dowiedz się ASP.NET AJAX](http://go.microsoft.com/fwlink/?LinkId=186475) dotyczące korzystania z usług sieci Web w ramach technologii AJAX.  
  
 Większość [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług może być udostępniany jako usługa zgodne z ASP.NET AJAX, dodając odpowiednie punktu końcowego ASP.NET AJAX.  
  
 Jeśli używasz programu Visual Studio, można użyć wbudowanych szablonu dla usługi WCF z włączoną obsługą technologii AJAX, dostępne w **Dodaj nowy element** okna dialogowego podczas pracy z witryn sieci Web ASP.NET lub aplikacji sieci Web.  
  
 Jeśli nie używasz szablony programu Visual Studio, istnieją dwa sposoby tworzenia punktu końcowego ASP.NET AJAX:  
  
-   Tworzenie punktu końcowego za pomocą aktywacji dynamicznego hosta bez użycia żadnej konfiguracji. Jest to najbardziej podstawowa rozwiązanie, jeśli znasz system konfiguracji usługi WCF. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).  
  
-   Dodawanie punktu końcowego interfejsu AJAX do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] za pomocą konfiguracji usługi. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).  
  
 Model programowania sieci Web, które są opisane w [programowania omówienie modelu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md) może być używany z usługami ASP.NET AJAX. W szczególności:  
  
-   Można użyć <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybutów, aby wybrać opcję zleceń HTTP GET i POST protokołu HTTP. Jeśli używana poprawnie, może to znacznie zwiększyć wydajność aplikacji. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Porady: Wybieranie między HTTP POST i HTTP GET żądania dla punktów końcowych AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md).  
  
-   Można użyć <xref:System.ServiceModel.Web.WebGetAttribute.ResponseFormat%2A> i <xref:System.ServiceModel.Web.WebInvokeAttribute.ResponseFormat%2A> właściwości, aby spowodować, że usługi zwrócić dane XML zamiast domyślnej JavaScript Object Notation (JSON). W ten sposób za pomocą kodu ASP.NET AJAX framework powoduje, że klient JavaScript do odbierania obiektu XML DOM.  
  
    > [!WARNING]
    >  Operacja ustawić typ zawartości do tekstu/xml, aby to zrobić. W przeciwnym razie klienta JavaScript otrzyma ciąg zawierający XML zamiast obiektu XML DOM.  
  
     Poniżej przedstawiono przykład operację, która zwraca dane XML z typem zawartości odpowiednio ustawione:  
  
    ```  
    [OperationContract, WebGet(ResponseFormat=WebMessageFormat.Xml)]  
    public XElement GetData()  
    {  
    XElement x;  
    //Get some data here...  
  
    WebOperationContext.Current.OutgoingResponse.ContentType = "text/xml";      
    return x;  
    }  
    ```  
  
-   Nie innych właściwości w <xref:System.ServiceModel.Web.WebGetAttribute> i <xref:System.ServiceModel.Web.WebInvokeAttribute> atrybuty można zmienić, jeśli wymagana jest zgodność z ASP.NET AJAX. Innych aspektów modelu programowania sieci Web można tak długo, jak konwencji wywoływania kodu ASP.NET AJAX nie zostały naruszone.  
  
 Niektóre dodatkowe szczegóły dotyczące obsługi interfejsu AJAX w wymagają bardziej zaawansowanych scenariuszy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zrozumienie:  
  
-   Aby zrozumieć, jak dane są przesyłane między klientem strony AJAX i [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi przy użyciu języka JavaScript i szczegółowe informacje o sposobie mapowania typów .NET Framework typy JavaScript, zobacz [obsługę JSON i inne formaty transferu danych](../../../../docs/framework/wcf/feature-details/support-for-json-and-other-data-transfer-formats.md) .  
  
-   Aby móc korzystać z programu ASP.NET, na przykład uwierzytelnianie za pomocą adresu URL i uzyskiwania dostępu do informacji o sesji programu ASP.NET, może chcesz włączyć tryb zgodności ASP.NET przy użyciu konfiguracji.  
  
 Punktów końcowych AJAX w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mogą być używane nawet bez ASP.NET AJAX framework. Wymaga zrozumienia obsługiwać architekturę obsługi technologii AJAX w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Omówienie tej architektury, zobacz [programowania modelu obiektów programu WCF Web HTTP](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md). Przykładowy kod prezentacja takie podejście, [usługa AJAX z formatami JSON i XML](../../../../docs/framework/wcf/samples/ajax-service-with-json-and-xml-sample.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Instrukcje: dodawanie punktu końcowego AJAX ASP.NET bez używania konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)  
 [Instrukcje: dodawanie punktu końcowego AJAX ASP.NET przy użyciu konfiguracji](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)  
 [Instrukcje: wybieranie między żądaniami HTTP POST i HTTP GET dla punktów końcowych AJAX ASP.NET](../../../../docs/framework/wcf/feature-details/http-post-and-http-get-requests-for-aspnet-ajax-endpoints.md)

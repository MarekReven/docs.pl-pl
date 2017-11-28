---
title: "Porady: Ustawianie nagłówków w żądaniu klienta (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, customizing requests
ms.assetid: 3d55168d-5901-4f48-8117-6c93da3ab5ae
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 62bd78c58f83e0fbe2a6d8ed08104b15e183001b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-headers-in-the-client-request-wcf-data-services"></a>Porady: Ustawianie nagłówków w żądaniu klienta (usługi danych WCF)
Jeśli używasz [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta do dostępu do usługi danych, która obsługuje [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)], Biblioteka klienta automatycznie ustawia wymagane nagłówki HTTP wiadomości żądania wysyłane do usługi danych. Biblioteka klienta nie może określić można ustawić nagłówków komunikatów, które są wymagane w niektórych przypadkach, takich jak kiedy usługa danych wymaga uwierzytelniania opartego na oświadczeniach lub plików cookie. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md#clientAuthentication). W takich przypadkach należy ręcznie ustawić nagłówki komunikatów w komunikacie żądania przed ich wysłaniem. W przykładzie w tym temacie przedstawiono sposób obsługi <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenie, aby dodać nowy nagłówek komunikat żądania, przed wysłaniem do usługi danych.  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md). Można również użyć [Northwind przykładowych danych usługi](http://go.microsoft.com/fwlink/?LinkId=187426) który jest opublikowany w [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web; te przykładowe dane usługi jest tylko do odczytu i zwraca błąd, próba zapisania zmian. Przykładowe dane usługi na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] witryny sieci Web umożliwia uwierzytelnianie anonimowe.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład rejestruje program obsługi <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzeń, a następnie wykonuje zapytanie usługi danych.  
  
> [!NOTE]
>  Jeśli usługa danych wymaga, należy ręcznie ustawić nagłówek komunikatu dla każdego żądania, należy wziąć pod uwagę rejestrowania programu obsługi <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzenia przez zastąpienie `OnContextCreated` usługi metody częściowej w kontenerze jednostek, który reprezentuje dane, które w Ten przypadek jest `NorthwindEntities`.  
  
[!code-csharp[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#registerheadersquery)]   
[!code-vb[Astoria Northwind Client#RegisterHeadersQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#registerheadersquery)]
  
## <a name="example"></a>Przykład  
 Następujące dojścia metody <xref:System.Data.Services.Client.DataServiceContext.SendingRequest> zdarzeń i dodaje nagłówek uwierzytelnienia do żądania.  
  
 [!code-csharp[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#onsendingrequest)]  
 [!code-vb[Astoria Northwind Client#OnSendingRequest](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#onsendingrequest)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usługi danych WCF](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)  
 [Biblioteka klienta usługi danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
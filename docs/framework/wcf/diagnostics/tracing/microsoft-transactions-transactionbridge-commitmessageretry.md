---
title: Microsoft.Transactions.TransactionBridge.CommitMessageRetry
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4abe01f0-6398-4fba-b2f3-c054b7f7e971
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58adacd909ad5254f9fb1e67b42f122e0ea01ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="microsofttransactionstransactionbridgecommitmessageretry"></a>Microsoft.Transactions.TransactionBridge.CommitMessageRetry
Ponowna próba przekazania wiadomości została wysłana do uczestnika, który nie odpowiada.  
  
## <a name="description"></a>Opis  
 Śledzone w razie potrzeby lokalnego Menedżera transakcji do wysłania wiadomości zatwierdzania do uczestnika podrzędnych, ponieważ nie otrzymano odpowiedzi w określonym czasie.  
  
## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Badania potencjalnych sieci lub produktu problemy, które uniemożliwiają dostarczanie na czas odpowiedzi.  Jeśli wiele z tych wiadomości są widoczne, może to oznaczać problemy związane z infrastrukturą lub nieprawidłowo długich czasów odpowiedzi. Problemy z obu znacząco zmniejsza przepływność transakcji w systemie.  
  
## <a name="see-also"></a>Zobacz też  
 [Śledzenie](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Rozwiązywanie problemów z aplikacją za pomocą śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)  
 [Administracja i diagnostyka](../../../../../docs/framework/wcf/diagnostics/index.md)

---
title: Dodawanie stanu online i offline
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05e5f51d-81b6-4c17-b364-9dda447a5fce
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1a9f4cf65febd955e69d81f8dbb8f97aaa24e68c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="adding-online-and-offline-status"></a>Dodawanie stanu online i offline
W wielu przypadkach jest ważna w przypadku aplikacji do monitorowania konkretne szczegółowe informacje o stanie połączenia kanał elementu równorzędnego. Te informacje można uzyskać przez wywołanie metody `GetProperty` metody wykonania <xref:System.ServiceModel.IOnlineStatus> interfejsu. Obiekt o implementację tego interfejsu można monitorować stan połączenia lub Zarejestruj się w celu obsługi zdarzeń, takich jak `OnOnline` i `OnOffline`i reagowania natychmiast wystąpienia zmian do stanu online.  
  
 W infrastrukturze kanału równorzędnego klienta uważa się być w trybie online, jeśli jest dołączona do przynajmniej jednego równorzędnego i w trybie offline w przeciwnym razie wartość. Może to być szczególnie przydatne w zarówno debugowanie tworzenie aplikacji lub wyświetlanie szczegółowych informacji dla użytkownika końcowego.  
  
> [!NOTE]
>  Program obsługi zdarzeń w trybie online należy najpierw upewnić się czy węzeł jest otwarte przed wysłaniem komunikaty.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
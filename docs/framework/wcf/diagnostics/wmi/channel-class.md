---
title: "Klasa kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 073f0a2a2731a08acd914a7dd85cb2b419d98128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="channel-class"></a>Klasa kanału
Kanał  
  
## <a name="syntax"></a>Składnia  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa kanału nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa kanału ma następujące właściwości.  
  
### <a name="localaddress"></a>LocalAddress  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Lokalny punkt końcowy kanału.  
  
### <a name="ref"></a>ref  
 Typ danych: punktu końcowego  
  
 Dostęp typu: tylko do odczytu  
  
 Łączy się z odwołaniem do punktu końcowego kanału.  
  
### <a name="remoteaddress"></a>RemoteAddress  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Zdalny adres skojarzony z kanałem.  
  
### <a name="sessionid"></a>SessionId  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator bieżącej sesji, jeśli istnieje.  
  
### <a name="type"></a>Typ  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Typ kanału.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.ChannelBase>

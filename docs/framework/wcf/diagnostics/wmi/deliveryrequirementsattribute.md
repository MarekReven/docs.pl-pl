---
title: DeliveryRequirementsAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e297bfc0499ea3ee8d3dd8395165ca22b2baa1de
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="deliveryrequirementsattribute"></a>DeliveryRequirementsAttribute
DeliveryRequirementsAttribute  
  
## <a name="syntax"></a>Składnia  
  
```  
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a>Metody  
 Element DeliveryRequirementsAttribute klasa nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Element DeliveryRequirementsAttribute klasa ma następujące właściwości:  
  
### <a name="queueddeliveryrequirements"></a>Pola QueuedDeliveryRequirements  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy wiązanie dla usługi obsługuje kontrakty.  
  
### <a name="requireordereddelivery"></a>RequireOrderedDelivery  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy wiązanie obsługuje uporządkowane komunikaty.  
  
### <a name="targetcontract"></a>TargetContract  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Kontrakt, którego dotyczy.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.DeliveryRequirementsAttribute>

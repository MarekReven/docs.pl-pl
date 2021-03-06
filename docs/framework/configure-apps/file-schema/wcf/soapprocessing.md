---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1aeb100e1b8e160d30566cd43d67cbf49c6b5c4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltsoapprocessinggt"></a>&lt;soapProcessing&gt;

Określa zachowanie punktu końcowego klienta używany do organizowania wiadomości między inne powiązanie typy i wersje komunikatów.

**\<System. ServiceModel >**   
&nbsp;&nbsp;**\<zachowania >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<zachowanie >**   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**

## <a name="syntax"></a>Składnia

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|                   | Opis |
| ----------------- | ----------- |
| `processMessages` | Wartość logiczna określająca, czy wiadomości powinny być przekazywane między wersjami wiadomości SOAP. |

### <a name="child-elements"></a>Elementy podrzędne

Brak

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [**\<zachowanie >**](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | Określa zachowanie punktu końcowego. |

## <a name="remarks"></a>Uwagi

Przetwarzania protokołu SOAP to proces, w których wiadomości są konwertowane między wersjami wiadomości.

[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Usługa routingu można przekonwertować wiadomości z jednego protokołu na inny. Jeśli wersje komunikatów przychodzących i wychodzących są różne, tworzona jest nowa wiadomość o poprawnej wersji. Przetwarzanie komunikatów z jednym <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` do innego odbywa się przez utworzenie nowej [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] komunikat, który zawiera część treści i odpowiednie nagłówków z przychodzącego [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] wiadomości. Nagłówki specyficznych dla adresowania lub które są zrozumiałe na poziomie routera, nie są używane podczas tworzenia nowej wiadomości WCF, ponieważ te nagłówki są albo inną wersję (w przypadku adresowania nagłówki) lub są przetwarzane w ramach Komunikacja między klientem a router.

Określa, czy nagłówek jest umieszczany w wiadomości wychodzącej jest określana przez czy została oznaczona jako rozumieć przeszła przychodzące warstwie kanału. Nagłówki, które nie są zrozumiałe (np. nagłówki niestandardowe) nie są usuwane i dlatego Przekaż za pośrednictwem usługi routingu przez kopiowane do wiadomości wychodzącej. Treść wiadomości jest kopiowany do wiadomości wychodzącej. Komunikat jest następnie wysyłane kanału wychodzącego, w tym momencie wszystkie nagłówki oraz innych danych koperty określonych na komunikat zostanie utworzona i dodać protokół/transport.

Takie kroki przetwarzania ma miejsce, gdy określono zachowania przetwarzania protokołu SOAP. To [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) zachowanie jest zachowanie punktu końcowego, który jest stosowany do wszystkich punktów końcowych klienta (wychodzące), podczas uruchamiania usługi routingu. Domyślnie [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowanie tworzy i dołącza nowy [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) zachowanie w przypadku `processMessages` ustawioną `true` dla każdego punkt końcowy klienta. Jeśli protokół usługi routingu nie zrozumieć lub chcesz zastąpić domyślne zachowanie przetwarzania, można wyłączyć przetwarzania dla całej usługi routingu lub tylko dla konkretnego punktów końcowych protokołu SOAP.  Aby wyłączyć przetwarzania dla całej usługi routingu dla wszystkich punktów końcowych SOAP, ustaw `soapProcessing` atrybutu [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowania `false`. Aby wyłączyć SOAP przetwarzania dla danego punktu końcowego, należy użyć tego zachowania i ustawić jej `processMessages` atrybutu `false`, następnie dołączyć tego zachowania do punktu końcowego nie ma domyślnego przetwarzania kodu w.  Gdy [ \<routingu >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) zachowanie konfiguruje usługi routingu, pominie ponowne zastosowanie zachowania punktu końcowego, ponieważ już istnieje.

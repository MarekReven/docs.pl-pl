---
title: "Porady: dostosowywanie powiązania dostarczane przez System"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f8b97862-e8bb-470d-8b96-07733c21fe26
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a9b048b5c57d174ac921793ee8677622b88a0595
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-customize-a-system-provided-binding"></a>Porady: dostosowywanie powiązania dostarczane przez System
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zawiera kilka powiązania dostarczane przez system, które umożliwiają konfigurowanie niektórych właściwości podstawowych elementów powiązania, ale nie wszystkie właściwości. W tym temacie przedstawiono sposób ustawiania właściwości do powiązania elementów do tworzenia niestandardowego powiązania.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]jak bezpośrednio utworzyć i skonfigurować elementy powiązania bez korzystania z wiązania dostarczane przez system, zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie i rozszerzanie wiązań niestandardowych, zobacz [rozszerzanie powiązań](../../../../docs/framework/wcf/extending/extending-bindings.md).  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składają się wszystkie powiązania z *elementów wiązania*. Każdy element powiązania jest pochodną <xref:System.ServiceModel.Channels.BindingElement> klasy. Powiązania dostarczane przez system, takich jak <xref:System.ServiceModel.BasicHttpBinding> utworzyć i skonfigurować własne elementy wiązania. W tym temacie przedstawiono sposób dostępu i zmiana właściwości tych elementów powiązania, które nie są bezpośrednio widoczne dla powiązania; w szczególności <xref:System.ServiceModel.BasicHttpBinding> klasy.  
  
 Poszczególne elementy znajdują się w kolekcji reprezentowany przez <xref:System.ServiceModel.Channels.BindingElementCollection> klasy i są dodawane w następującej kolejności: przepływu transakcji, niezawodnej sesji zabezpieczeń, złożone dupleksowy, jednokierunkowe zabezpieczenia strumienia, kodowanie komunikatu i transportu. Należy pamiętać, że nie wszystkie elementy na liście są wymagane w każdym powiązania. Elementy wiązania zdefiniowane przez użytkownika może również zostać wyświetlony w tej kolekcji element powiązania i musi występować w tej samej kolejności, w sposób opisany wcześniej. Na przykład transportu zdefiniowane przez użytkownika musi być ostatnim elementem kolekcji element powiązania.  
  
 <xref:System.ServiceModel.BasicHttpBinding> Klasa zawiera trzy elementy powiązania:  
  
1.  Opcjonalne zabezpieczeń powiązania elementu, albo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> klasy używane z transportu HTTP (zabezpieczeniami na poziomie wiadomości) lub <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> klasy, która jest używana podczas warstwy transportowej zawiera zabezpieczeń, w tym przypadku transportu HTTPS jest używany.  
  
2.  Kodera komunikatów wymagane powiązanie elementu, albo <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> lub <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>.  
  
3.  Transport wymagane powiązanie elementu, albo <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, lub <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
 W tym przykładzie mamy utworzyć wystąpienia powiązania, generowanie *niestandardowego powiązania* z niej informacji, sprawdź elementy niestandardowego powiązania, a gdy okaże się element powiązania protokołu HTTP, możemy jego `KeepAliveEnabled` właściwości `false`. `KeepAliveEnabled` Właściwość nie jest uwidaczniana bezpośrednio na `BasicHttpBinding`, więc musi utworzyć niestandardowego powiązania, przejdź do elementu powiązania i ustaw dla tej właściwości.  
  
### <a name="to-modify-a-system-provided-binding"></a>Aby zmodyfikować powiązania dostarczane przez system  
  
1.  Utwórz wystąpienie <xref:System.ServiceModel.BasicHttpBinding> klasy, a jego tryb zabezpieczeń na poziomie wiadomości.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#1)]
     [!code-vb[C_HowTo_ChangeStandardBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#1)]  
  
2.  Tworzenie niestandardowego powiązania z wiązania i Utwórz <xref:System.ServiceModel.Channels.BindingElementCollection> klasy z jednej z właściwości niestandardowego powiązania.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#2)]
     [!code-vb[C_HowTo_ChangeStandardBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#2)]  
  
3.  Pętli <xref:System.ServiceModel.Channels.BindingElementCollection> klasy, i do wyszukania <xref:System.ServiceModel.Channels.HttpTransportBindingElement> klasy, ustaw jej <xref:System.ServiceModel.Channels.HttpTransportBindingElement.KeepAliveEnabled%2A> właściwości `false`.  
  
     [!code-csharp[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_changestandardbinding/cs/program.cs#3)]
     [!code-vb[C_HowTo_ChangeStandardBinding#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_changestandardbinding/vb/program.vb#3)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Powiązania niestandardowe](../../../../docs/framework/wcf/extending/custom-bindings.md)

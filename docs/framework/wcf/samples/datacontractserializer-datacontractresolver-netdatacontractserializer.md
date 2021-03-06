---
title: "Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5477f11b5bc00ff4816b3fac8d61b254ebaf5ba0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Używanie elementów DataContractSerializer i DataContractResolver do udostępniania funkcji elementu NetDataContractSerializer
W tym przykładzie pokazano sposób stosowania <xref:System.Runtime.Serialization.DataContractSerializer> odpowiedni <xref:System.Runtime.Serialization.DataContractResolver> zapewnia te same funkcje co <xref:System.Runtime.Serialization.NetDataContractSerializer>. W tym przykładzie przedstawiono sposób tworzenia odpowiednie <xref:System.Runtime.Serialization.DataContractResolver> i dodawaniu go do <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="sample-details"></a>Szczegóły próbki  
 <xref:System.Runtime.Serialization.NetDataContractSerializer>różni się od <xref:System.Runtime.Serialization.DataContractSerializer> w jednym ze sposobów ważne: <xref:System.Runtime.Serialization.NetDataContractSerializer> zawiera informacje o typie CLR w serializacji XML, a <xref:System.Runtime.Serialization.DataContractSerializer> nie. W związku z tym <xref:System.Runtime.Serialization.NetDataContractSerializer> mogą być używane tylko w przypadku, gdy zarówno serializację i deserializację kończy się udostępnianie tych samych typów CLR. Jednak zaleca się użyć <xref:System.Runtime.Serialization.DataContractSerializer> , ponieważ jego wydajność jest lepszym rozwiązaniem niż <xref:System.Runtime.Serialization.NetDataContractSerializer>. Można zmienić informacje, które jest serializowany w <xref:System.Runtime.Serialization.DataContractSerializer> przez dodanie <xref:System.Runtime.Serialization.DataContractResolver> do niego.  
  
 Ten przykład zawiera dwa projekty. Pierwszy projekt używa <xref:System.Runtime.Serialization.NetDataContractSerializer> szeregowania obiektu. Drugi projekt używa <xref:System.Runtime.Serialization.DataContractSerializer> z <xref:System.Runtime.Serialization.DataContractResolver> zapewnienie te same funkcje co pierwszy projekt.  
  
 Poniższy przykładowy kod przedstawia implementację niestandardowego <xref:System.Runtime.Serialization.DataContractResolver> o nazwie `MyDataContractResolver` który został dodany do <xref:System.Runtime.Serialization.DataContractSerializer> w projekcie DCSwithDCR.  
  
```  
class MyDataContractResolver : DataContractResolver  
{  
    private XmlDictionary dictionary = new XmlDictionary();  
  
    public MyDataContractResolver()  
    {  
    }  
  
    // Used at deserialization  
    // Allows users to map xsi:type name to any Type   
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)  
    {  
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);  
        if (type == null)  
        {  
            type = Type.GetType(typeName + ", " + typeNamespace);  
        }  
        return type;  
    }  
  
    // Used at serialization  
    // Maps any Type to a new xsi:type representation  
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)  
    {  
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);  
        if (typeName == null || typeNamespace == null)  
        {  
            XmlDictionary dictionary = new XmlDictionary();  
            typeName = dictionary.Add(dataContractType.FullName);  
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);  
        }  
    }  
}  
```  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Przy użyciu [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otwórz plik rozwiązania DCRSample.sln.  
  
2.  Kliknij prawym przyciskiem myszy plik rozwiązania i wybierz polecenie **właściwości**.  
  
3.  W **strony właściwości rozwiązania** okna dialogowego, w obszarze **wspólne właściwości**, **projekt startowy**, wybierz pozycję **wiele projektów startowych:**.  
  
4.  Obok pozycji **DCSwithDCR** projektu, zaznacz **Start** z **akcji** listy rozwijanej.  
  
5.  Obok pozycji **NetDCS** projektu, zaznacz **Start** z **akcji** listy rozwijanej.  
  
6.  Kliknij przycisk **OK** aby zamknąć okno dialogowe.  
  
7.  Aby tworzyć rozwiązania, naciśnij kombinację klawiszy CTRL + SHIFT + B.  
  
8.  Aby uruchomić rozwiązanie, naciśnij klawisze CTRL + F5.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
## <a name="see-also"></a>Zobacz też

---
title: "Transakcje przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6081fb02-c0f2-483d-97b8-f3b7dc03011d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d9cc01d929421b8065a3df21374150bc68fd968
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-transactions"></a>Transakcje przepływu pracy
[!INCLUDE[wf1](../../../includes/wf1-md.md)]zapewnia obsługę uczestniczących w <xref:System.Transactions> transakcji przy użyciu <xref:System.Activities.Statements.TransactionScope> działania do określania zakresu transakcyjne jednostkę pracy. Gdy <xref:System.Transactions.TransactionScope?displayProperty=nameWithType> muszą być wypełnione jawnie <xref:System.Activities.Statements.TransactionScope?displayProperty=nameWithType> niejawnie wywołania ukończyć działania transakcji po pomyślnym zakończeniu. Żadnych działań, które są zawarte w <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope> działania uczestniczyć w transakcji. WF można przepływ transakcji w przepływie pracy za pośrednictwem <xref:System.ServiceModel.Activities.TransactedReceiveScope> działania. Podobnie jak <xref:System.Activities.Statements.TransactionScope> działania, wszystkie działania zawarte w <xref:System.ServiceModel.Activities.TransactedReceiveScope.Body%2A> uczestniczy w transakcji. WF zapewnia zależnych od tego działania na <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType> działa z obiema <xref:System.Activities.Statements.TransactionScope> i <xref:System.ServiceModel.Activities.TransactedReceiveScope>. Jeśli działania dostarczane przez system nie dotyczą wszystkich wymagań, działań niestandardowych można skonstruować za pomocą <xref:System.Activities.RuntimeTransactionHandle> umożliwiające przepływ zaawansowane i scenariuszy kontroli transakcji.  
  
 W poniższym przykładzie pobierana z [podstawowego elementu TransactionScope](../../../docs/framework/windows-workflow-foundation/samples/basic-transactionscope.md) przykładowy przepływ pracy jest tworzony, składające się z <xref:System.Activities.Statements.Sequence> działanie, które występują działania podrzędne, w tym <xref:System.Activities.Statements.TransactionScope> działania. <xref:System.Activities.Statements.TransactionScope.Body%2A> Działania <xref:System.Activities.Statements.TransactionScope> wykonać w obrębie transakcji zainicjowane przez <xref:System.Activities.Statements.TransactionScope> działania.  
  
```csharp  
static Activity ScenarioOne()  
{  
    return new Sequence  
    {  
        Activities =  
        {  
            new WriteLine { Text = "    Begin workflow" },  
  
            new TransactionScope  
            {  
                Body = new Sequence  
                {  
                    Activities =   
                    {  
                        new WriteLine { Text = "    Begin TransactionScope" },  
  
                        new PrintTransactionId(),  
  
                        new TransactionScopeTest(),  
  
                        new WriteLine { Text = "    End TransactionScope" },  
                    },  
                },  
            },  
  
            new WriteLine { Text = "    End workflow" },  
        }  
    };  
}  
```  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]podstawowe [transakcji](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) przykłady oraz scenariusz na podstawie [transakcji](../../../docs/framework/windows-workflow-foundation/samples/transactions.md) próbek. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]o używaniu <xref:System.ServiceModel.Activities.TransactedReceiveScope>, zobacz [przepływu transakcji do i z usług przepływu pracy](../../../docs/framework/wcf/feature-details/flowing-transactions-into-and-out-of-workflow-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.Statements.TransactionScope>  
 <xref:System.Transactions.TransactionScope>  
 <xref:System.Transactions.Transaction.Current%2A?displayProperty=nameWithType>

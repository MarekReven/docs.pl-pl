---
title: "Porady: wywołanie wbudowane funkcje zdefiniowane przez użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: f80d4327-b6a5-4aa8-a743-e95d09a2a02e
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f84d6c2c75844ab265259339ed8f72e42419f63a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-call-user-defined-functions-inline"></a>Porady: wywołanie wbudowane funkcje zdefiniowane przez użytkownika
Mimo że można wywołać wbudowane funkcje zdefiniowane przez użytkownika, funkcji, które są uwzględnione w zapytaniu, których wykonanie została odroczona nie są wykonywane, dopóki zapytanie jest wykonywane. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 Podczas wywoływania tej samej funkcji poza zapytaniem, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tworzy prostego zapytania z wyrażenia wywołania metody. Oto składnia SQL (parametr `@p0` jest powiązany ze stałą przekazano):  
  
```  
SELECT dbo.ReverseCustName(@p0)  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tworzy następujące czynności:  
  
 [!code-csharp[DLinqUDFS#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#4)]
 [!code-vb[DLinqUDFS#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#4)]  
  
## <a name="example"></a>Przykład  
 W następujących [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania, zostanie wyświetlony wbudowanego wywołanie metody generowanej funkcji zdefiniowanej przez użytkownika `ReverseCustName`. Funkcja nie została wykonana natychmiast, ponieważ wykonywanie zapytania została odroczona. SQL zbudowanych dla tego zapytania przekłada się na wywołanie funkcji zdefiniowanej przez użytkownika w bazie danych (zobacz kod SQL następującej kwerendy).  
  
 [!code-csharp[DLinqUDFS#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#5)]
 [!code-vb[DLinqUDFS#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#5)]  
  
```  
SELECT [t0].[ContactName],  
    dbo.ReverseCustName([t0].[ContactTitle]) AS [Title]  
FROM [Customers] AS [t0]  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Funkcje zdefiniowane przez użytkownika](../../../../../../docs/framework/data/adonet/sql/linq/user-defined-functions.md)

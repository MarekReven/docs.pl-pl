---
title: "Porady: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktom współbieżności"
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
ms.assetid: d2cda293-1e2f-4878-af0e-5aaf0d092120
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0c65299f48db3ba727cece673e6a7df2d9cd8872
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-specify-which-members-are-tested-for-concurrency-conflicts"></a>Porady: Określanie, które elementy członkowskie są sprawdzane pod kątem konfliktom współbieżności
Zastosuj jedną z trzech typów wyliczeniowych do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwość <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu, aby określić, którzy członkowie mają być uwzględniane w aktualizacji sprawdza wykrywanie konfliktów optymistycznej współbieżności.  
  
 <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> (Zamapować w czasie projektowania) jest używana razem z funkcji współbieżności środowiska wykonawczego w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Aby uzyskać więcej informacji, zobacz [optymistycznej współbieżności: omówienie](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
> [!NOTE]
>  Oryginalne wartości elementu członkowskiego są porównywane z bieżącym stanem bazy danych, tak długo, jak żaden element członkowski jest oznaczony jako `IsVersion=true`. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
 Aby uzyskać przykłady kodu, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
### <a name="to-always-use-this-member-for-detecting-conflicts"></a>Zawsze używaj tego elementu członkowskiego do wykrywania konfliktów  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartości właściwości do `Always`.  
  
### <a name="to-never-use-this-member-for-detecting-conflicts"></a>Nigdy nie należy używać tego elementu członkowskiego do wykrywania konfliktów  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartości właściwości do `Never`.  
  
### <a name="to-use-this-member-for-detecting-conflicts-only-when-the-application-has-changed-the-value-of-the-member"></a>Aby użyć tego elementu członkowskiego do wykrywania konfliktów tylko wtedy, gdy aplikacja została zmieniona wartość elementu członkowskiego  
  
1.  Dodaj <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> właściwości <xref:System.Data.Linq.Mapping.ColumnAttribute> atrybutu.  
  
2.  Ustaw <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A> wartości właściwości do `WhenChanged`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład określa, że `HomePage` obiekty nigdy nie należy podawać podczas sprawdzania aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Data.Linq.Mapping.ColumnAttribute.UpdateCheck%2A>.  
  
 [!code-csharp[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.mapping.updatecheck/cs/northwind.cs#1)]
 [!code-vb[System.Data.Linq.Mapping.UpdateCheck#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.mapping.updatecheck/vb/northwind.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zarządzanie konfliktami zmian](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Tworzenie i przesyłanie zmian danych](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)

---
title: "Obowiązki dewelopera w Zastępowanie domyślnego zachowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6909ddd-e053-46a8-980c-0e12a9797be1
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 7de5dbcad14ebfd253ba99f03a8d77e768f29941
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="responsibilities-of-the-developer-in-overriding-default-behavior"></a>Obowiązki dewelopera w Zastępowanie domyślnego zachowania
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie wymusza następujące wymagania, ale zachowanie jest niezdefiniowana, jeśli te wymagania nie zostały spełnione.  
  
-   Nie należy wywołać metodę zastępującą <xref:System.Data.Linq.DataContext.SubmitChanges%2A> lub <xref:System.Data.Linq.Table%601.Attach%2A>. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]zgłasza wyjątek, jeśli te metody są wywoływane w metodzie zastąpienia.  
  
-   Zastąpienie metody nie można uruchomić, Zatwierdź lub zatrzymać transakcji. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> Jest wykonywane w ramach transakcji. Wewnętrzny transakcji zagnieżdżonej może zakłócać transakcji zewnętrznej. Obciążenia zastąpienie metody można rozpocząć transakcji, tylko wtedy, gdy określają one, czy operacja nie jest obecnie wykonywana w <xref:System.Transactions.Transaction>.  
  
-   Zastąpienie metody powinny Wykonaj mapowanie dotyczy optymistycznej współbieżności. Metoda przesłaniająca powinien zgłosić <xref:System.Data.Linq.ChangeConflictException> gdy wystąpi konflikt optymistycznej współbieżności. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Przechwytuje tego wyjątku, dzięki czemu można poprawnie przetworzyć <xref:System.Data.Linq.DataContext.SubmitChanges%2A> opcji na <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
-   Utwórz (`Insert`) i `Update` zastąpienie metody powinny ponownie przepływ wartości kolumn generowanych przez bazę danych do odpowiednich elementów członkowskich obiektu po pomyślnym zakończeniu operacji.  
  
     Na przykład jeśli `Order.OrderID` jest zamapowany na kolumny tożsamości (*autoincrement* klucza podstawowego), a następnie `InsertOrder()` Metoda przesłaniająca musi pobrać identyfikator wygenerowany bazy danych i ustaw `Order.OrderID` członka ten identyfikator. Ponadto członkowie sygnatury czasowej muszą zostać zaktualizowane do wartości baza danych wygenerowała sygnatury czasowej, aby upewnić się, że zaktualizowanych obiektów są spójne. Awaria propagację wartości generowanych przez bazy danych może spowodować niezgodność między bazy danych i obiektów śledzone przez <xref:System.Data.Linq.DataContext>.  
  
-   Jest odpowiedzialny za użytkownika do wywołania poprawne dynamicznego interfejsu API. Na przykład w aktualizacji zastąpić metodę, tylko <xref:System.Data.Linq.DataContext.ExecuteDynamicUpdate%2A> może zostać wywołana. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]nie wykrywa ani nie Sprawdź, czy wywoływanej metody dynamicznej zgodna odpowiednich operacji. Jeśli nie ma zastosowania metoda jest wywoływana (na przykład <xref:System.Data.Linq.DataContext.ExecuteDynamicDelete%2A> dla obiekt aktualizacji), wyniki są niezdefiniowane.  
  
-   Na koniec metodę zastępującą powinien wykonać określonej operacji. Semantyka [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] operacji, takich jak wczesny ładowania, odłożone ładowanie, i <xref:System.Data.Linq.DataContext.SubmitChanges%2A>) wymagają zastąpienia w stanie określonej usługi. Na przykład obciążenia musi zostać zastąpiona po prostu zwracającej pustą kolekcję bez sprawdzenia, czy zawartość w bazie danych prawdopodobnie spowoduje niespójność danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Dostosowywanie operacji wstawiania, aktualizowania i usuwania](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)

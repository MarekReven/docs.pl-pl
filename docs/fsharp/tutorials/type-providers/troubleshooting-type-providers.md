---
title: "Rozwiązywanie problemów z dostawcami typów"
description: "Wykrywa potencjalne rozwiązania problemów, które prawdopodobnie mogą wystąpić podczas używania dostawcy typów w F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 44533045-9862-43c5-81d9-3e05157e975a
ms.openlocfilehash: 2b54454d7950dfdd6512d849fd739f505ef3317d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="troubleshooting-type-providers"></a>Rozwiązywanie problemów z dostawcami typów

W tym temacie opisano oraz zapewnia potencjalne rozwiązania problemów, które najprawdopodobniej będą występować podczas korzystania z dostawcy typów.


## <a name="possible-problems-with-type-providers"></a>Możliwe problemy przy pomocy dostawcy typów
Jeśli wystąpi problem podczas pracy z dostawców typów, można przejrzeć w tabeli poniżej najbardziej typowych rozwiązań.



|Problem|Sugerowanych akcji|
|-------|-----------------|
|**Zmiany schematu**. Typ pracy dostawców najlepiej, gdy schematu źródła danych jest stabilna. Jeśli dodasz danych tabeli lub kolumny lub innego zmiany tego schematu, dostawca typów nie rozpoznaje automatycznie tych zmian.|Czyszczenie lub ponownie skompilować projekt. Aby wyczyścić projektu, wybierz **kompilacji**, **wyczyść** *ProjectName* na pasku menu. Aby ponownie skompilować projekt, wybierz **kompilacji**, **odbudować** *ProjectName* na pasku menu. Te akcje zresetowanie wszystkich stanów dostawcy typu i wymuszanie dostawcy, aby ponownie połączyć się ze źródłem danych i uzyskiwanie informacji o schemacie zaktualizowane.|
|**Błąd połączenia**. Adres URL lub ciąg połączenia jest nieprawidłowy, sieć nie działa lub źródła danych lub usługi jest niedostępny.|Usługi sieci web lub usługi OData możesz spróbować adresu URL w przeglądarce Internet Explorer, aby sprawdzić, czy adres URL jest poprawny i czy usługa jest dostępna. Dla ciągu połączenia bazy danych, można użyć narzędzia połączenia danych w **Eksploratora serwera** Aby sprawdzić, czy parametry połączenia są prawidłowe i baza danych jest dostępne. Po przywróceniu połączenia, należy wyczyścić lub ponownie skompilować projekt, tak aby dostawca typów zostanie ponownie połączyć się z siecią.|
|**Nieprawidłowe poświadczenia**. Musi mieć prawidłowe uprawnienia do danych źródła lub usługą sieci web.|Połączenia SQL nazwę użytkownika i hasło, które są określone w pliku ciągu lub konfiguracji połączenia musi być prawidłowy dla bazy danych. Jeśli używasz uwierzytelniania systemu Windows musi mieć dostęp do bazy danych. Administrator bazy danych można zidentyfikować uprawnień potrzebnych do dostępu do wszystkich baz danych i każdego elementu w bazie danych.<br /><br />Usługi sieci web lub usługi danych musi mieć odpowiednie poświadczenia. Większość dostawców typów Podaj obiektu DataContext, który zawiera właściwość poświadczeń można ustawić z odpowiednią nazwą użytkownika i klucza dostępu.|
|**Nieprawidłowa ścieżka**. Ścieżka do pliku jest nieprawidłowa.|Sprawdź, czy ścieżka jest poprawna i czy plik istnieje. Ponadto należy odpowiednio Oferta żadnych backlashes w ścieżce lub użyj ciągu dosłownego wyrażenia lub potrójne cudzysłowy ciągu.|

## <a name="see-also"></a>Zobacz też
[Dostawcy typów](index.md)

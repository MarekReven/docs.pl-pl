---
title: "Krotki — przewodnik C#"
description: "Dowiedz się więcej o typy nazwane i nienazwane spójnej kolekcji w języku C#"
keywords: .NET, .NET core, C#
author: BillWagner
ms-author: wiwagn
ms.date: 11/23/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 58f76332a8f3717fe10788382552598d6693e7e3
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="c-tuple-types"></a>Typy krotki C# #

C# krotek są typy zdefiniowane przez użytkownika przy użyciu składni lightweight. Zalety obejmują składni prostszy, reguły konwersji na podstawie numeru (nazywane Kardynalność) i typy elementów i spójne zasady kopii i przypisania. Jako zależnościami spójne kolekcje nie obsługują niektórych idioms obiektowej skojarzono dziedziczenie. Przegląd w sekcji można uzyskać [krotek, co jest nowego w języku C# 7](whats-new/csharp-7.md#tuples) tematu.

W tym temacie dowiesz się języka zasady krotek w języku C# 7 różne sposoby stosowania ich i początkowej wskazówki na temat pracy z spójnych kolekcji.

> [!NOTE]
> Nowe funkcje krotek wymagają <xref:System.ValueTuple> typów.
> Należy dodać pakiet NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) aby można było używać go na platformach, które nie uwzględniają typów.
>
> Efekt jest podobny do innych funkcji języka, które zależą od typów dostarczane w ramach. Przykłady obejmują `async` i `await` polegania na `INotifyCompletion` interfejsu i LINQ polegania na `IEnumerable<T>`. Jednak mechanizm dostarczania zmienia się zgodnie z .NET staje się coraz więcej niezależnie od platformy. .NET Framework nie mogą zawsze dostarczany na tym samym okresach jako kompilatora języka. Gdy nowe funkcje językowe bazuje na nowe typy, te typy będą dostępne jako pakietów NuGet podczas wysłać funkcje języka. Jak te nowe typy dodane do standardowego interfejsu API programu .NET i dostarczane w ramach struktury, wymaganie pakietu NuGet zostaną usunięte.

Zacznijmy od przyczyny dodawania nowych obsługi spójnej kolekcji. Metody zwracają pojedynczego obiektu. Krotki umożliwiają łatwiejsze pakietu wielu wartości w tym pojedynczego obiektu.

.NET Framework ma już ogólnego `Tuple` klasy. Te klasy, jednak ma dwa główne ograniczenia. Dla jednego `Tuple` ich właściwości o nazwie klasy `Item1`, `Item2`i tak dalej. Te nazwy przenoszenia żadne informacje semantyczne. Korzystanie z tych `Tuple` typów nie obsługuje komunikacji znaczenie poszczególnych właściwości. Nowe funkcje językowe umożliwiają deklarowanie i użycie semantycznie łatwy do rozpoznania nazwy elementów w spójnej kolekcji.

Inną kwestią jest to, że `Tuple` klasy są typy referencyjne. Przy użyciu jednej z `Tuple` typy oznacza Alokacja obiektów. Na gorąco ścieżki to ma zauważalnego wpływu na wydajność aplikacji. W związku z tym obsługi języka krotek wykorzystuje nowe `ValueTuple` struktury.

Aby uniknąć tych braki, można utworzyć `class` lub `struct` do przenoszenia wielu elementów. Niestety jest więcej pracy, a jest ukrywany z celem projektu. Tworzenie `struct` lub `class` oznacza definiowania typu z danych i zachowania. Wiele razy po prostu chcesz przechowywać wiele wartości w jeden obiekt.

Funkcje języka i `ValueTuple` struktury ogólne wymuszać reguły, że nie można dodać żadnych zachowanie (metody) do tych typów spójnej kolekcji.
Wszystkie `ValueTuple` typy są *modyfikowalną struktury*. Każdy członek pola jest publicznym polem. Dzięki temu ich bardzo uproszczonego. Jednakże oznacza to, że nie należy używać krotek których immutability jest ważna.

Spójne kolekcje są obie kontenerów danych prostszy i bardziej elastyczne niż `class` i `struct` typów. Przyjrzyjmy się różnic.

## <a name="named-and-unnamed-tuples"></a>Krotki nazwane i nienazwane

`ValueTuple` Struktura zawiera pola o nazwie `Item1`, `Item2`, `Item3` i tak dalej, podobna do właściwości zdefiniowane w istniejących `Tuple` typów.
Te nazwy są tylko nazwy można użyć dla *nienazwane krotek*. Gdy wszystkie nazwy pól alternatywnych do krotki nie zostanie określona, zostanie utworzona krotka bez nazwy:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Spójna kolekcja znajdująca się w poprzednim przykładzie została zainicjowana przy użyciu stałe literałów i nie będą mieć nazwy elementów utworzone przy użyciu *krotki pole Nazwa projekcje* w języku C# 7.1.

Podczas inicjowania krotka można jednak użyć nowe funkcje językowe, które zapewniają lepszą nazwy do każdego pola. Dzięki temu tworzy *o nazwie krotki*.
Nazwane krotek jeszcze elementy o nazwie `Item1`, `Item2`, `Item3` i tak dalej.
Ale ma także synonimy dla każdego z tych elementów, które mają być nazwane.
Określanie nazw dla każdego elementu do tworzenia nazwanego spójnej kolekcji. Jednym ze sposobów jest do określenia nazwy w ramach inicjalizacji spójnej kolekcji:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

Te synonimy są obsługiwane przez kompilator i język tak, aby można było używać o nazwie krotek efektywnie. IDEs i Redaktorzy mogą odczytywać te nazwy semantycznych przy użyciu interfejsów API Roslyn. Dzięki temu można odwołać się elementy o nazwie spójnej kolekcji za pomocą tych nazw semantyczne w dowolnym miejscu tego samego zestawu. Kompilator zastępuje nazwy zdefiniowany przez użytkownika z `Item*` odpowiedniki podczas generowania skompilowanych danych wyjściowych. Skompilowany Microsoft pośredniego Language (MSIL) nie zawiera nazwy został przyznany tych elementów.

Począwszy od 7.1 C#, nazw pól dla krotka mogą być dostarczane z zmienne używaną do inicjalizacji spójnej kolekcji. Jest to określane jako  **[inicjatory projekcji krotki](#tuple-projection-initializers)**. Poniższy kod tworzy spójną kolekcję o nazwie `accumulation` z elementami `count` (liczba całkowita), i `sum` (wartość o podwójnej precyzji).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilator muszą komunikować się tych nazw utworzone krotek, do którego są zwracane z publicznej metody lub właściwości. W takich przypadkach dodaje kompilator <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> atrybutu w metodzie. Ten atrybut zawiera <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> listę właściwości, która zawiera nazwy do poszczególnych elementów w spójnej kolekcji.

> [!NOTE]
> Narzędzia deweloperskie, takiego jak Visual Studio również odczytać metadane i podaj IntelliSense i innych funkcji przy użyciu nazwy pól metadanych.

Ważne jest, aby zrozumieć bazowy podstawowe informacje na temat nowych krotek i `ValueTuple` typu, aby zrozumieć zasady przypisywania o nazwie krotek ze sobą.

## <a name="tuple-projection-initializers"></a>Inicjatory projekcji spójnej kolekcji

Ogólnie rzecz biorąc inicjatory projekcji krotki pracy przy użyciu nazwy zmiennej lub pola z prawej stronie instrukcji inicjowania spójnej kolekcji.
Jeśli jawna nazwa została podana, który ma pierwszeństwo przed dowolną nazwę planowane. Na przykład w inicjatorze następujące elementy są `explicitFieldOne` i `explicitFieldTwo`, a nie `localVariableOne` i `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Dla dowolnego pola, w których nie podano nazwy jawne odpowiednie nazwy niejawne będzie można utworzyć projekcji. Należy pamiętać, że nie jest wymagane zapewnienie semantycznego nazwy jawnie lub niejawnie. Następujące inicjatora będą mieć nazwy pola `Item1`, którego wartość jest `42` i `StringContent`, którego wartość wynosi "Odpowiedź wszystko":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

Istnieją dwa warunki gdzie candidate nazwy pól nie są rzutowany na pole spójnej kolekcji:

1. Gdy nazwa candidate jest nazwą zastrzeżone spójnej kolekcji. Przykłady obejmują `Item3`, `ToString` lub `Rest`.
1. Gdy nazwa candidate jest duplikatem inną nazwę pola krotki jawnych ani niejawnych.

Te warunki uniknąć niejednoznaczności. Te nazwy spowodowałoby niejednoznaczności, jeśli zostały one używane jako nazwy pola dla pola w spójnej kolekcji. Żadna z tych warunków Przyczyna kompilacji czasu błędów. Zamiast tego elementów bez nazwy planowanego nie masz nazwy semantycznego zaprojektowana dla nich.  W poniższych przykładach pokazano następujące warunki:

[!code-csharp[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Ponieważ wyniesie istotne zmiany dla kod napisany za pomocą języka C# 7.0, gdy projekcje nazwę pola krotki nie były dostępne tych sytuacji nie powodują błędy kompilatora.

## <a name="assignment-and-tuples"></a>Przypisanie i spójnych kolekcji

Język obsługuje przypisania między typami spójnej kolekcji, które mają taką samą liczbę elementów i niejawne konwersje typów dla każdego z tych elementów. Inne konwersje nie są uznawane za przydziałów. Oto typy przydziałów, które mogą między typami spójnej kolekcji.

Należy wziąć pod uwagę następujące zmienne używane w poniższych przykładach:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

Pierwsze dwie zmienne `unnamed` i `anonymous` nie mają semantycznego nazw określonych elementów. Nazwy pól są `Item1` i `Item2`.
Ostatnie dwie zmienne `named` i `differentName` semantycznego nazwach podanych elementów. Należy pamiętać, że te dwie spójne kolekcje mają różne nazwy dla elementów.

Wszystkie cztery te krotki mają taką samą liczbę elementów (określanych jako "Kardynalność") i typy te elementy są identyczne. W związku z tym wszystkie te przydziały działają:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Należy zauważyć, że nazwy krotki nie są przypisane. Wartości elementów są przypisywane kolejności elementów w spójnej kolekcji.

Spójne kolekcje różnych typów lub numerów elementów nie są można przypisać:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Wartości zwracane krotek jako — metoda

Jest jednym z najbardziej typowych zastosowań krotek jako wartość zwracaną metody. Przejdźmy przykładem. Oblicza odchylenie standardowe dla sekwencji liczb tej metody należy wziąć pod uwagę:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Poniższe przykłady obliczeniowe odchylenie standardowe Niepoprawione próbki.
> Wzór odchylenia standardowego poprawione próbki będzie rozmieszczona sumę kwadratów różnic od średniej przez (N-1) zamiast N, `Average` jest — metoda rozszerzenia. Aby uzyskać więcej informacji na temat różnic między te formuły odchylenie standardowe, zapoznaj się tekst statystyk.

Wynika to Podręcznikowy formułę odchylenie standardowe. Generuje prawidłowa odpowiedź, ale jest bardzo mało wydajne implementacji. Ta metoda wylicza kolejność dwa razy: raz, aby utworzyć średnią i raz, aby utworzyć średnią kwadratu różnicy średniej.
(Pamiętaj, że zapytań LINQ są oceniane w trybie opóźnienia, tak obliczania różnic ze średniej i średnią różnic sprawia, że tylko jedno wyliczenie).

Brak alternatywnych formuła, której oblicza odchylenie standardowe za pomocą tylko jedno wyliczenie sekwencji.  Te obliczenia tworzy dwie wartości, zgodnie z jego wylicza sekwencji: Suma wszystkich elementów w sekwencji i sumę każdej wartości kwadrat:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Ta wersja wylicza kolejność dokładnie raz. Jednak nie jest bardzo do ponownego użycia kodu. Jak można kontynuować pracę, przekonasz się, że wiele różnych obliczenia statystyczne używać liczba elementów w sekwencji, sum sekwencji i suma kwadratów sekwencji. Załóżmy Refaktoryzuj tę metodę i napisanie metody narzędzia, która tworzy wszystkie trzy tych wartości.

Jest to, gdzie krotki mają bardzo przydatne. 

Teraz zaktualizuj tę metodę, aby trzy wartości obliczonych podczas wyliczania są przechowywane w spójnej kolekcji. Tworzącą tej wersji:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Obsługa Refactoring programu Visual Studio ułatwia wyodrębnić funkcja statystyki podstawowe do metody prywatnej. Który umożliwia `private static` metodę, która zwraca typ krotki z trzech wartości `Sum`, `SumOfSquares`, i `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
Język umożliwia kilka więcej opcji, których można użyć, jeśli chcesz wprowadzić kilka zmian szybkie ręcznie. Najpierw należy użyć `var` deklaracji zainicjować wynik krotki `ComputeSumAndSumOfSquares` wywołania metody. Można również utworzyć trzy zmienne dyskretnego wewnątrz `ComputeSumAndSumOfSquares` metody. Wersja ostateczna znajduje się poniżej:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Tej wersji ostatecznej może służyć do dowolnej metody, która wymaga wartości te trzy lub dowolny podzbiór.

Język obsługuje inne opcje zarządzania nazwy elementów w tych metod zwracających spójnej kolekcji.

Można usunąć nazwy pól z deklaracji zwracanej wartości i zwraca krotka bez nazwy:

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

Muszą spełnić pola to tuple jako `Item1`, `Item2`, i `Item3`.
Zaleca się podanie semantycznego nazw elementów krotek zwrócony z metody.

Inny idiom, gdzie może być bardzo przydatne krotek jest podczas tworzenia zapytań LINQ wynik końcowy w przypadku projekcji, który zawiera niektóre, ale nie wszystkie właściwości obiektów wybierane.

Wyniki zapytania będą tradycyjnie projektu w sekwencji obiektów, które były typu anonimowego. Wiele ograniczeń, które przedstawione głównie, ponieważ typy anonimowe można nie znajdują się nazwy w zwracany typ metody. Przy użyciu alternatywnych `object` lub `dynamic` jako typ wyniku pochodzi z kosztami znaczących wydajności.

Zwracanie sekwencji krotki typu jest łatwe i nazwy i typy elementów są dostępne w czasie kompilacji i za pomocą narzędzia IDE.
Rozważmy na przykład aplikację zadań do wykonania. Można zdefiniować klasę podobny do następującego do reprezentowania pojedynczy wpis na liście ToDo:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Twojej aplikacji dla urządzeń przenośnych może obsługiwać compact formę bieżącego zadań do wykonania, która wyświetla tylko tytuł. Czy kwerendy LINQ spowodowałoby projekcji który obejmuje tylko identyfikator i tytuł. Metoda, która zwraca sekwencję krotek bardzo dobrze wyraża tego projektu:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> W języku C# 7.1 projekcje krotki umożliwiają tworzenie nazwanego krotek za pomocą elementów, w sposób podobny do właściwości nazw typów anonimowych. W powyższym kodzie `select` instrukcja w projekcji zapytań tworzy spójnej kolekcji, który ma elementy `ID` i `Title`.

Spójna kolekcja znajdująca się o nazwie może być częścią podpisu. Umożliwia kompilatorowi i narzędzia IDE zapewniają statyczne sprawdzania, czy używasz wynik poprawnie. Spójnej kolekcji o nazwie również przenosi informacje statycznego typu, a więc nie trzeba używać kosztowne czas wykonywania funkcji, takich jak odbicia lub dynamiczne powiązanie do pracy z wyników.

## <a name="deconstruction"></a>Deconstruction

Można rozpakować wszystkie elementy w krotce przez *deconstructing* zwróconych przez metodę spójnej kolekcji. Istnieją trzy różne sposoby deconstructing spójnych kolekcji.  Po pierwsze można jawnie deklarować typu każdego pola w nawiasy, aby utworzyć zmienne discrete dla poszczególnych elementów w spójnej kolekcji:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Niejawnie wpisane zmienne dla każdego pola w krotce może deklarować także za pomocą `var` — słowo kluczowe poza nawiasy:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Jest również używać `var` — słowo kluczowe z dowolnego lub wszystkich deklaracji zmiennych wewnątrz nawiasów. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Należy pamiętać, że nie można użyć określonego typu poza nawiasów, nawet w przypadku każdego pola w spójnej kolekcji ma ten sam typ.

Można deconstruct spójnych kolekcji zawierający istniejących deklaracji również:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  Nie można mieszać istniejących deklaracji z deklaracjami wewnątrz nawiasów. Na przykład następujące jest niedozwolone: `(var x, y) = MyMethod();`. To powoduje błąd CS8184, ponieważ *x* jest zadeklarowana wewnątrz nawiasów i *y* wcześniej jest zadeklarowany w innych miejscach.

### <a name="deconstructing-user-defined-types"></a>Typy zdefiniowane przez użytkownika deconstructing

Dowolny typ krotki można deconstructed, jak pokazano powyżej. Jest również łatwo włączyć deconstruction na dowolnego typu zdefiniowanego przez użytkownika (klasy, struktury lub nawet interfejsów).

Autor typ można określić jedną lub więcej `Deconstruct` metod, które przypisać wartości do dowolnej liczby `out` zmienne reprezentującego elementy danych, które tworzą typu. Na przykład następująca `Person` definiuje typ `Deconstruct` metodę, która deconstructs obiektu osoby do elementów reprezentujących imię i nazwisko:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda deconstruct umożliwia przypisanie z `Person` na dwa ciągi, reprezentujący `FirstName` i `LastName` właściwości:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Można włączyć deconstruction nawet w przypadku typów, które autorów.
`Deconstruct` Metoda może być — metoda rozszerzenia rozpakowuje danych dostępnych elementów członkowskich obiektu. Poniżej przedstawiono przykład `Student` Typ pochodny `Person` typ i metodę rozszerzenia, które deconstructs `Student` do trzech zmiennych, reprezentujący `FirstName`, `LastName` i `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

A `Student` ma teraz dostępne dwa `Deconstruct` metody: zadeklarować metody rozszerzenia dla `Student` typy i członek `Person` typu. Zarówno znajdują się w zakresie oraz umożliwia `Student` do można deconstructed do zmiennych dwóch lub trzech.
Jeśli student można przypisać do trzech zmiennych, imię, ostatni nazwę i GPA są wszystkie zwracane. Jeśli student przydzielić dwie zmienne, zwracane są tylko imię i nazwisko.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Należy zwrócić szczególną uwagę na zdefiniowanie wielu `Deconstruct` metody w klasie lub hierarchia klas. Wiele `Deconstruct` metod, które mają taką samą liczbę `out` parametry szybko może powodować niejednoznaczności. Obiekty wywołujące nie można łatwo wywołać żądaną `Deconstruct` metody.

W tym przykładzie jest minimalnym możliwości niejednoznaczne wywołanie ponieważ `Deconstruct` metodę `Person` ma dwa produkt wyjściowy parametry i `Deconstruct` metoda `Student` ma trzy.

## <a name="conclusion"></a>Wniosek 

Nowa funkcja języka i biblioteki obsługi o nazwie krotek ułatwia do pracy z projektami używające struktury danych, przechowywać wiele elementów, które nie określają zachowanie, jak klasy i struktury. Jest łatwy i zwięzłe używany spójnych kolekcji dla tych typów. Pobierz wszystkie zalety kontrola typów statycznych, bez konieczności tworzenia typów przy użyciu na pełniejsze `class` lub `struct` składni. Mimo tego, że są one najbardziej przydatny w przypadku metody narzędziowe, które są `private`, lub `internal`. Tworzenie typów zdefiniowanych przez użytkownika, albo `class` lub `struct` typy gdy publicznej metody zwróci wartość, która ma wiele elementów.

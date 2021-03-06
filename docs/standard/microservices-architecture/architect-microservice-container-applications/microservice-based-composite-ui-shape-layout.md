---
title: "Tworzenie złożonego interfejsu użytkownika oparte na mikrousług, w tym visual kształtu interfejsu użytkownika i układu generowane przez wiele mikrousług"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Tworzenie złożonego interfejsu użytkownika oparte na mikrousług, w tym visual kształtu interfejsu użytkownika i układu generowane przez wiele mikrousług"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 12b170e9d4c46fbb697f988596af6566d33099a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Tworzenie złożonego interfejsu użytkownika oparte na mikrousług, w tym visual kształtu interfejsu użytkownika i układu generowane przez wiele mikrousług

Architektura Mikrousług często rozpoczyna się od obsługi logiki i danych po stronie serwera. Jednak bardziej zaawansowane podejściem jest projektowanie interfejsu użytkownika oparta na mikrousług oraz aplikacji. Oznacza to, o złożonego interfejsu użytkownika utworzone przez mikrousług, zamiast mikrousług na serwerze i po prostu wbudowanymi klienta aplikacji przez wykorzystywanie mikrousług. Takie podejście może być mikrousług, tworzonych z zarówno logiki i wizualnej reprezentacji.

Rysunek 4-20 pokazuje prostsze eksploatującego właśnie mikrousług z wbudowanymi klienta aplikacji. Oczywiście może zostać usługi platformy ASP.NET MVC Between produkujących HTML i JavaScript. Liczba jest uproszczenie, który wyróżnia się, że masz jednego klienta (wbudowanymi) mikrousług, który właśnie skupić się na logikę i dane, a nie na kształtu interfejsu użytkownika (HTML i JavaScript) korzystanie z interfejsu użytkownika.

![](./media/image20.png)

**Rysunek 4-20**. Wbudowanymi aplikacji interfejsu użytkownika, wykorzystywanie mikrousług zaplecza

Z kolei złożonego interfejsu użytkownika jest dokładnie generowane i składane przez mikrousług, samodzielnie. Niektóre mikrousług stacji visual kształt określonych obszarów interfejsu użytkownika. Najważniejsza różnica polega na składniki interfejsu użytkownika klienta (na przykład klasy TS) na podstawie szablonów, czy ViewModel danych kształtowania-interfejsu użytkownika dla tych szablonów pochodzi z każdym mikrousługi.

W momencie uruchamiania aplikacji klienta poszczególne składniki interfejsu użytkownika klienta (na przykład klasy TypeScript) rejestruje się o stanie dostarczać ViewModels w danym scenariuszu mikrousługi infrastruktury. W przypadku mikrousługi zmiany kształtu, również zmiany interfejsu użytkownika.

Rysunek 4-21 zawiera wersję tego podejścia złożonego interfejsu użytkownika. To jest uproszczone, ponieważ może mieć inne mikrousług, który agregowania szczegółowego części oparte na różnych technik — zależy on od jest konstruowany podejście tradycyjnych sieci web (platformy ASP.NET MVC) lub SPA (jednej strony aplikacji).

![](./media/image21.png)

**Rysunek 4-21**. Przykład złożonych aplikacji interfejsu użytkownika w kształcie przez mikrousług zaplecza

Każdy z tych mikrousług kompozycji interfejsu użytkownika mogą być podobne do małych bramy interfejsu API. Jednak w takim przypadku każdy jest odpowiedzialny za mały obszar interfejsu użytkownika.

Złożone podejście interfejsu użytkownika, który jest wymuszany przez mikrousług może być wyzwaniem więcej lub mniej tak, w zależności od tego, jakie technologii interfejsu użytkownika używasz. Na przykład nie będzie używać tych samych metod do tworzenia aplikacji sieci web tradycyjnych, używanej do tworzenia SPA lub natywnych aplikacji mobilnej (tak jak podczas tworzenia aplikacji platformy Xamarin, które mogą być trudniejsze dla tej metody).

[EShopOnContainers](http://aka.ms/MicroservicesArchitecture) Przykładowa aplikacja korzysta z wbudowanymi podejście interfejsu użytkownika dla wielu powodów. Po pierwsze jest wprowadzenie do mikrousług oraz kontenerów. Złożonego interfejsu użytkownika jest bardziej zaawansowane, ale również wymaga dalszych złożoności podczas projektowania i opracowywania interfejsu użytkownika. Po drugie, eShopOnContainers zapewnia natywnej aplikacji mobilnej oparte na platformie Xamarin, która będzie bardziej złożone na kliencie C\# po stronie.

Jednak firma Microsoft zachęca do użycia następujące odwołania, aby dowiedzieć się więcej na temat złożone interfejsu użytkownika oparta na mikrousług.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Złożony interfejs użytkownika za pomocą programu ASP.NET (w szczególności Workshop)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. Wbudowanymi frontonu w architekturze Mikrousług**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. Klucz tajny lepsze kompozycji interfejsu użytkownika**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **VIKTOR Farcic. W tym składniki frontonu sieci Web do Mikrousług**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Zarządzanie frontonu w architekturze Mikrousług**\
    [*http://Allegro.tech/2016/03/Managing-Frontend-in-the-microservices-Architecture.HTML*](http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Poprzednie] (mikrousług adresowanie usług registry.md) [dalej] (odporność wysoki — dostępność microservices.md)

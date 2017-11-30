---
title: "Implementowanie mikrousługi warstwy aplikacji przy użyciu interfejsu API sieci Web"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie mikrousługi warstwy aplikacji przy użyciu interfejsu API sieci Web"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="f2423-104">Implementowanie mikrousługi warstwy aplikacji przy użyciu interfejsu API sieci Web</span><span class="sxs-lookup"><span data-stu-id="f2423-104">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="f2423-105">Przy użyciu iniekcji zależności na iniekcję obiektów infrastruktury do warstwy aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2423-105">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="f2423-106">Jak wspomniano wcześniej, można zaimplementować jako część artefaktu tworzysz, takie jak w projekcie interfejsu API sieci Web lub projektu aplikacji sieci web MVC warstwy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2423-106">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="f2423-107">W przypadku mikrousługi skompilowanej za pomocą platformy ASP.NET Core warstwy aplikacji będzie zazwyczaj biblioteki interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f2423-107">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="f2423-108">Aby oddzielić wkrótce z platformy ASP.NET Core (swoją infrastrukturę oraz kontrolerach) w kodzie warstwy aplikacji niestandardowych, można również umieścić warstwy aplikacji w bibliotece klas oddzielnych, ale jest to opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="f2423-108">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="f2423-109">Na przykład kod warstwy aplikacji porządkowania mikrousługi bezpośrednio jest zaimplementowany jako część **Ordering.API** projekt (projekt interfejsu API platformy ASP.NET Core sieci Web), rysunek jako pokazano 9-19.</span><span class="sxs-lookup"><span data-stu-id="f2423-109">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="f2423-110">**Rysunek 9-19**.</span><span class="sxs-lookup"><span data-stu-id="f2423-110">**Figure 9-19**.</span></span> <span data-ttu-id="f2423-111">Warstwa aplikacji w projekcie interfejsu API programu Ordering.API platformy ASP.NET Core sieci Web</span><span class="sxs-lookup"><span data-stu-id="f2423-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="f2423-112">Platformy ASP.NET Core obejmuje prostą [wbudowanych kontenera IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentowane przez interfejsu IServiceProvider) obsługującej iniekcji konstruktora domyślnie i program ASP.NET udostępnia pewnych usług za pośrednictwem Podpisane.</span><span class="sxs-lookup"><span data-stu-id="f2423-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="f2423-113">Termin korzysta z platformy ASP.NET Core *usługi* dla każdego z typów rejestrowania, które będą wstrzyknięte przez Podpisane.</span><span class="sxs-lookup"><span data-stu-id="f2423-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="f2423-114">Należy skonfigurować usługi wbudowanych kontenerów w ConfigureServices metody w klasie uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2423-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="f2423-115">Zależności są implementowane w usługach, które wymaga typu.</span><span class="sxs-lookup"><span data-stu-id="f2423-115">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="f2423-116">Zazwyczaj mają wstrzyknięcia zależności, które implementują obiektów infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f2423-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="f2423-117">Zależność bardzo typowy iniekcję to repozytorium.</span><span class="sxs-lookup"><span data-stu-id="f2423-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="f2423-118">Jednak można wstrzyknąć innych zależności infrastruktury, który może być.</span><span class="sxs-lookup"><span data-stu-id="f2423-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="f2423-119">W przypadku prostszych implementacji może bezpośrednio uruchomić obiektu wzorzec jednostki pracy (obiektu EF DbContext), ponieważ DBContext jest również implementacji obiektów trwałości infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="f2423-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="f2423-120">W poniższym przykładzie widać, jak oprogramowanie .NET Core wprowadza obiekty wymagane repozytorium za pośrednictwem konstruktora.</span><span class="sxs-lookup"><span data-stu-id="f2423-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="f2423-121">Klasa jest programem obsługi, które omówimy w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f2423-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

<span data-ttu-id="f2423-122">Klasa używa wprowadzony repozytoria do wykonania transakcji i utrwalić zmiany stanu.</span><span class="sxs-lookup"><span data-stu-id="f2423-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="f2423-123">Nie ma znaczenia, czy w tej klasy jest programem obsługi, metoda kontrolera interfejsu API platformy ASP.NET Core sieci Web, czy [usługi aplikacji DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="f2423-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="f2423-124">Ostatecznie jest prostą klasę, który używa repozytoriów, jednostek domeny i innych koordynacji aplikacji w sposób podobny do obsługi polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="f2423-125">Taki sam sposób dla wszystkich wymienionych klas, jak pokazano w przykładzie przy użyciu Podpisane oparte na konstruktorze działa iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="f2423-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="f2423-126">Rejestrowanie typów wdrożenia zależności i interfejsów lub obiektów abstrakcyjnych</span><span class="sxs-lookup"><span data-stu-id="f2423-126">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="f2423-127">Przed użyciem obiekty dodane za pomocą konstruktorów, musisz wiedzieć, gdzie można zarejestrować interfejsów i klasy, które powodują powstanie obiektów do klasy Twojej aplikacji za pośrednictwem Podpisane.</span><span class="sxs-lookup"><span data-stu-id="f2423-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="f2423-128">(Takich jak Podpisane na podstawie konstruktora, jak pokazano wcześniej.)</span><span class="sxs-lookup"><span data-stu-id="f2423-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="f2423-129">Za pomocą wbudowanych kontenera IoC pochodzącymi z platformy ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f2423-129">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="f2423-130">Korzystając z wbudowanego kontenera IoC pochodzącymi z platformy ASP.NET Core, zarejestruj się typów, który chcesz wstawić w metodzie ConfigureServices w pliku Startup.cs, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="f2423-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="f2423-131">Najbardziej typowe wzorzec po rejestrowanie typów w kontenerze Inwersja kontroli można zarejestrować dwa typy — interfejs i jego klasa implementacji pokrewne.</span><span class="sxs-lookup"><span data-stu-id="f2423-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="f2423-132">W przypadku żądania obiektu z kontenera IoC za pomocą dowolnego konstruktora, następnie zażądać obiektu określonego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="f2423-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="f2423-133">Na przykład w poprzednim przykładzie, ostatni wiersz stwierdza, że gdy dowolne z konstruktorów zależy od IMyCustomRepository (interfejsu lub abstrakcji), kontenera IoC będzie wstrzyknąć wystąpienie implementacji MyCustomSQLServerRepository Klasa.</span><span class="sxs-lookup"><span data-stu-id="f2423-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="f2423-134">Za pomocą biblioteki Scrutor typy automatycznej rejestracji</span><span class="sxs-lookup"><span data-stu-id="f2423-134">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="f2423-135">Używając Podpisane w .NET Core, możesz mieć możliwość skanowania zestawu i automatyczne rejestrowanie jego typów przez Konwencję.</span><span class="sxs-lookup"><span data-stu-id="f2423-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="f2423-136">Ta funkcja nie jest obecnie dostępna w ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2423-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="f2423-137">Można jednak użyć [Scrutor](https://github.com/khellang/Scrutor) biblioteki w tym.</span><span class="sxs-lookup"><span data-stu-id="f2423-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="f2423-138">Takie podejście jest wygodny w przypadku wielu typów, które muszą być zarejestrowane w Twojej kontenera IoC.</span><span class="sxs-lookup"><span data-stu-id="f2423-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f2423-139">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="f2423-139">Additional resources</span></span>

-   <span data-ttu-id="f2423-140">**Matthew króla. Usługi w zarejestrowani Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="f2423-140">**Matthew King. Registering services with Scrutor**
[*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="f2423-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="f2423-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="f2423-142">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f2423-142">GitHub repo.</span></span>
    [<span data-ttu-id="f2423-143">*https://github.com/khellang/Scrutor*</span><span class="sxs-lookup"><span data-stu-id="f2423-143">*https://github.com/khellang/Scrutor*</span></span>](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="f2423-144">Przy użyciu Autofac jako kontenera IoC</span><span class="sxs-lookup"><span data-stu-id="f2423-144">Using Autofac as an IoC container</span></span>

<span data-ttu-id="f2423-145">Można również użyć dodatkowe kontenery Inwersja kontroli i podłącz je do potoku platformy ASP.NET Core, tak jak porządkowania mikrousługi w eShopOnContainers, który używa [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="f2423-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="f2423-146">Korzystając z Autofac zwykle należy zarejestrować typy za pośrednictwem modułów, dzięki której można podzielić typów rejestracji między wiele plików, w zależności od lokalizacji użytkownika typy, tak samo, jak można używać typów aplikacji rozproszone na wielu bibliotek klas.</span><span class="sxs-lookup"><span data-stu-id="f2423-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="f2423-147">Na przykład poniżej przedstawiono [modułu aplikacji Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) dla [interfejsu API sieci Web Ordering.API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projektu z typami można wstrzyknąć.</span><span class="sxs-lookup"><span data-stu-id="f2423-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule
    :Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="f2423-148">Proces rejestracji i pojęcia są bardzo podobne do sposób z wbudowanych kontenerem platformy ASP.NET Core dla systemu iOS można zarejestrować typy, ale składni, korzystając z Autofac różni się nieco.</span><span class="sxs-lookup"><span data-stu-id="f2423-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core iOS container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="f2423-149">W przykładowym kodzie abstrakcji IOrderRepository został zarejestrowany oraz klasa implementacji OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="f2423-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="f2423-150">Oznacza to, że zawsze, gdy Konstruktor jest deklarowanie zależności za pomocą abstrakcji IOrderRepository lub interfejsu, kontenera IoC będzie wstrzyknąć wystąpienia klasy OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="f2423-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="f2423-151">Typ zakresu wystąpienia określa, jak wystąpienia są współużytkowane przez żądania dla tej samej usługi lub zależności.</span><span class="sxs-lookup"><span data-stu-id="f2423-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="f2423-152">Po wysłaniu żądania jest zależność, kontenera IoC może zwrócić następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f2423-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="f2423-153">Jednego wystąpienia na okres istnienia zakresu (określone w kontenerze platformy ASP.NET Core IoC jako *zakres*).</span><span class="sxs-lookup"><span data-stu-id="f2423-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="f2423-154">Nowe wystąpienie na zależność (określone w kontenerze platformy ASP.NET Core IoC jako *przejściowa*).</span><span class="sxs-lookup"><span data-stu-id="f2423-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="f2423-155">Pojedyncze wystąpienie współużytkowana przez wszystkie obiekty przy użyciu kontenera IoC (określone w kontenerze platformy ASP.NET Core IoC jako *pojedyncze*).</span><span class="sxs-lookup"><span data-stu-id="f2423-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f2423-156">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="f2423-156">Additional resources</span></span>

-   <span data-ttu-id="f2423-157">**Wprowadzenie do iniekcji zależności w platformy ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="f2423-157">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="f2423-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="f2423-158">**Autofac.**</span></span> <span data-ttu-id="f2423-159">Oficjalna dokumentacja.</span><span class="sxs-lookup"><span data-stu-id="f2423-159">Official documentation.</span></span>
    [<span data-ttu-id="f2423-160">*http://docs.autofac.org/en/Latest/*</span><span class="sxs-lookup"><span data-stu-id="f2423-160">*http://docs.autofac.org/en/latest/*</span></span>](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="f2423-161">**Torre de la Cesarowi. Porównywanie okresy istnienia usługi kontenera platformy ASP.NET Core IoC z zakresami wystąpienia kontenera Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="f2423-161">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="f2423-162">Implementowanie wzorce polecenia i program obsługi poleceń</span><span class="sxs-lookup"><span data-stu-id="f2423-162">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="f2423-163">W przykładzie Podpisane za pomocą konstruktora przedstawionym w poprzedniej sekcji kontenera IoC został wstrzyknięcie repozytoria za pośrednictwem Konstruktor w klasie.</span><span class="sxs-lookup"><span data-stu-id="f2423-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="f2423-164">Ale dokładnie gdzie zostały one dodane?</span><span class="sxs-lookup"><span data-stu-id="f2423-164">But exactly where were they injected?</span></span> <span data-ttu-id="f2423-165">W przypadku prostego interfejsu API sieci Web (na przykład mikrousługi katalogu w eShopOnContainers) można wstrzyknąć na poziomie kontrolerów MVC, w Konstruktorze kontrolera.</span><span class="sxs-lookup"><span data-stu-id="f2423-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="f2423-166">Jednak w początkowej kodu w tej sekcji ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) klasy z usługi Ordering.API w eShopOnContainers), iniekcja zależności odbywa się za pośrednictwem konstruktora konkretnego polecenia Program obsługi.</span><span class="sxs-lookup"><span data-stu-id="f2423-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="f2423-167">Daj nam wyjaśnić programu obsługi poleceń jest i dlaczego warto jej używać.</span><span class="sxs-lookup"><span data-stu-id="f2423-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="f2423-168">Wzorzec polecenia leżą jest powiązany z wzorca CQRS, który został wprowadzony wcześniej w tym przewodniku.</span><span class="sxs-lookup"><span data-stu-id="f2423-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="f2423-169">CQRS ma dwie strony.</span><span class="sxs-lookup"><span data-stu-id="f2423-169">CQRS has two sides.</span></span> <span data-ttu-id="f2423-170">Pierwszy obszar jest zapytania za pomocą uproszczonego zapytań z [Dapper](https://github.com/StackExchange/dapper-dot-net) ORM micro wyjaśniono wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f2423-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="f2423-171">Drugi ma poleceń, które są punkt początkowy dla transakcji i kanał wejściowy z poza usługi.</span><span class="sxs-lookup"><span data-stu-id="f2423-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="f2423-172">Jak pokazano w rysunku 9-20, wzorzec jest oparta na akceptowanie poleceń z po stronie klienta, przetwarzania je zgodnie z regułami modelu domeny, a na koniec utrwalanie stanów transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2423-172">As shown in Figure 9-20, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="f2423-173">**Rysunek 9-20**.</span><span class="sxs-lookup"><span data-stu-id="f2423-173">**Figure 9-20**.</span></span> <span data-ttu-id="f2423-174">Widok wysokiego poziomu poleceń lub "transakcyjne po stronie" we wzorcu CQRS</span><span class="sxs-lookup"><span data-stu-id="f2423-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="f2423-175">Klasy poleceń</span><span class="sxs-lookup"><span data-stu-id="f2423-175">The command class</span></span>

<span data-ttu-id="f2423-176">Polecenie jest żądaniem systemu do wykonywania akcji zmieniającej stan systemu.</span><span class="sxs-lookup"><span data-stu-id="f2423-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="f2423-177">Polecenia są konieczne i powinny być przetwarzane tylko raz.</span><span class="sxs-lookup"><span data-stu-id="f2423-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="f2423-178">Ponieważ polecenia priorytetów, są zwykle nazywane ze zleceniem w trybie stylu (na przykład "Utwórz" lub "Aktualizuj"), i może zawierać typu agregacji, na przykład CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="f2423-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="f2423-179">W przeciwieństwie do zdarzenia polecenie nie jest faktów z przeszłości; jest tylko żądania, a w związku z tym można odmówić.</span><span class="sxs-lookup"><span data-stu-id="f2423-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="f2423-180">Polecenia można pochodzi z interfejsu użytkownika w wyniku inicjowanie żądanie użytkownika lub Menedżera procesu podczas Menedżera procesu jest kierowanie agregacji do wykonania akcji.</span><span class="sxs-lookup"><span data-stu-id="f2423-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="f2423-181">Istotne cechy polecenia jest, że powinien on tylko raz przetworzony przez jednego odbiorcę.</span><span class="sxs-lookup"><span data-stu-id="f2423-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="f2423-182">Jest tak, ponieważ polecenie jest jednej akcji lub transakcji, które należy wykonać w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2423-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="f2423-183">Na przykład tego samego polecenia tworzenia kolejności nie powinny być przetwarzane więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="f2423-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="f2423-184">Jest to ważna różnica między poleceń i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f2423-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="f2423-185">Zdarzenia mogą być przetwarzane wiele razy, ponieważ wiele systemów lub mikrousług mogą być zainteresowani zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="f2423-186">Ponadto jest ważne, że polecenie przetwarzane tylko raz w przypadku, gdy polecenie nie jest idempotentności.</span><span class="sxs-lookup"><span data-stu-id="f2423-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="f2423-187">Polecenie jest idempotentności, jeśli jego mogą być wykonywane wiele razy bez zmiany wyników, z powodu charakteru polecenia lub ze względu na sposób system obsługi polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="f2423-188">Jest dobrym rozwiązaniem, aby Twoje polecenia i aktualizuje idempotentności, gdy sens w ramach reguł biznesowych użytkownika domeny i invariants.</span><span class="sxs-lookup"><span data-stu-id="f2423-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="f2423-189">Na przykład do użycia w tym samym przykładzie, jeśli jakiegokolwiek powodu (logika ponowień, przejęcie itp.) tego samego polecenia CreateOrder osiągnie system wielokrotnie, można zidentyfikować je i upewnij się, nie należy tworzyć wielu zamówień.</span><span class="sxs-lookup"><span data-stu-id="f2423-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="f2423-190">Aby to zrobić, należy dołączyć określonego rodzaju tożsamości w operacjach i ustalić, czy polecenie lub aktualizacji został już przetworzony.</span><span class="sxs-lookup"><span data-stu-id="f2423-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="f2423-191">Wyślij polecenie do jednego odbiorcę; polecenie nie jest opublikować.</span><span class="sxs-lookup"><span data-stu-id="f2423-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="f2423-192">Publikowanie jest dla zdarzeń integracji, które stanu fakt — coś się nie stało i mogą być interesujące dla odbiorcy zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f2423-192">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="f2423-193">W przypadku zdarzeń wydawcy ma nie problemów, o których odbiorcy uzyskać zdarzenia lub co robią go.</span><span class="sxs-lookup"><span data-stu-id="f2423-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="f2423-194">Ale zdarzeń integracji inny wątek już wprowadzone w poprzednich sekcjach.</span><span class="sxs-lookup"><span data-stu-id="f2423-194">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="f2423-195">Polecenie jest realizowana za pomocą klasy, która zawiera pola danych lub kolekcji wszystkie informacje, które są potrzebne w celu wykonania tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="f2423-196">Polecenie jest specjalnym rodzajem z danych Transfer obiektu (DTO), które jest używane wyłącznie do żądania zmiany lub transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2423-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="f2423-197">Samo polecenie opiera się na dokładnie informacje potrzebne do przetwarzania polecenia i nic więcej.</span><span class="sxs-lookup"><span data-stu-id="f2423-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="f2423-198">W poniższym przykładzie pokazano uproszczony klasy CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="f2423-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="f2423-199">To jest niezmienialny polecenia, który jest używany w porządkowania mikrousługi w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="f2423-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string City { get; private set; }

    [DataMember]
    public string Street { get; private set; }

    [DataMember]
    public string State { get; private set; }

    [DataMember]
    public string Country { get; private set; }

    [DataMember]
    public string ZipCode { get; private set; }

    [DataMember]
    public string CardNumber { get; private set; }

    [DataMember]
    public string CardHolderName { get; private set; }

    [DataMember]
    public DateTime CardExpiration { get; private set; }

    [DataMember]
    public string CardSecurityNumber { get; private set; }

    [DataMember]
    public int CardTypeId { get; private set; }

    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="f2423-200">Zasadniczo klasy poleceń zawiera wszystkie dane potrzebne do przeprowadzania transakcji firm za pomocą obiektów modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="f2423-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="f2423-201">W związku z tym polecenia są po prostu struktur danych, które zawierają dane tylko do odczytu i nie zachowanie.</span><span class="sxs-lookup"><span data-stu-id="f2423-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="f2423-202">Nazwa polecenia wskazuje jej celem.</span><span class="sxs-lookup"><span data-stu-id="f2423-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="f2423-203">W wielu językach takich jak C\#, polecenia są reprezentowane jako klasy, ale nie są one true klas w tym sensie, rzeczywista obiektowo.</span><span class="sxs-lookup"><span data-stu-id="f2423-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="f2423-204">Jako dodatkowe właściwości polecenia są niezmienne, ponieważ jest oczekiwane wykorzystanie są przetwarzane bezpośrednio przez modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="f2423-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="f2423-205">Potrzebują oni zmieniać podczas ich przewidywanego okresu istnienia.</span><span class="sxs-lookup"><span data-stu-id="f2423-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="f2423-206">W języku C\# klasy immutability można osiągnąć, ponieważ nie ma żadnych ustawiające lub innych metod, które spowodują zmianę stanu wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="f2423-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="f2423-207">Na przykład klasa polecenia do tworzenia kolejności jest prawdopodobnie podobne pod względem danych kolejność, według której ma zostać utworzona, ale prawdopodobnie nie ma potrzeby takie same atrybuty.</span><span class="sxs-lookup"><span data-stu-id="f2423-207">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="f2423-208">Na przykład CreateOrderCommand nie ma identyfikator zamówienia, ponieważ kolejność nie został jeszcze utworzony.</span><span class="sxs-lookup"><span data-stu-id="f2423-208">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="f2423-209">Wiele klas polecenie może być prosty, wymagania dotyczące niektórych stanu, który musi zostać zmienione tylko kilka pól.</span><span class="sxs-lookup"><span data-stu-id="f2423-209">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="f2423-210">Wyniesie przypadku tylko w przypadku zmiany stanu zlecenia od "w toku" do "płatnej" lub "wysłane" przy użyciu polecenia podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="f2423-210">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="f2423-211">Niektóre deweloperzy tworzą żądania interfejsu użytkownika w nich obiekty niezależnie od ich DTOs polecenia, ale jest to wystarczy preferencji.</span><span class="sxs-lookup"><span data-stu-id="f2423-211">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="f2423-212">Jest niewygodny separacji nie wiele wartości dodanej, a obiekty są prawie dokładnie tego samego kształtu.</span><span class="sxs-lookup"><span data-stu-id="f2423-212">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="f2423-213">Na przykład w eShopOnContainers, polecenia pochodzi bezpośrednio z po stronie klienta.</span><span class="sxs-lookup"><span data-stu-id="f2423-213">For instance, in eShopOnContainers, the commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="f2423-214">Klasa obsługi polecenia</span><span class="sxs-lookup"><span data-stu-id="f2423-214">The Command Handler class</span></span>

<span data-ttu-id="f2423-215">Należy zaimplementować klasę programu obsługi określonego polecenia dla każdego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-215">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="f2423-216">To działanie wzorzec i jest którym będziesz używać obiektów repozytorium infrastruktury, obiektów domeny i obiektu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-216">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="f2423-217">Program obsługi poleceń w rzeczywistości jest centralnym warstwy aplikacji pod względem CQRS i DDD.</span><span class="sxs-lookup"><span data-stu-id="f2423-217">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="f2423-218">Jednak całą logikę domeny powinny być zawarte w klasach domeny — w ramach korzenie agregacji (jednostek głównego), jednostek podrzędnych lub [usług domenowych w usłudze](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale nie w ciągu programu obsługi poleceń, który jest klasy z aplikacji warstwy.</span><span class="sxs-lookup"><span data-stu-id="f2423-218">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="f2423-219">Program obsługi poleceń odebrało polecenie i uzyskuje wynik z zagregowaną, która jest używana.</span><span class="sxs-lookup"><span data-stu-id="f2423-219">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="f2423-220">Wynik powinien być pomyślnego wykonania polecenia lub wystąpił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f2423-220">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="f2423-221">W przypadku wyjątku stanu systemu należy bez zmian.</span><span class="sxs-lookup"><span data-stu-id="f2423-221">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="f2423-222">Program obsługi poleceń zazwyczaj wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f2423-222">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="f2423-223">Odbiera obiekt polecenia, takich jak DTO (z [mediatora](https://en.wikipedia.org/wiki/Mediator_pattern) lub innego obiektu infrastruktury).</span><span class="sxs-lookup"><span data-stu-id="f2423-223">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="f2423-224">Jest sprawdzane, czy to polecenie jest nieprawidłowa (Jeśli nie jest zweryfikowany przez mediatora).</span><span class="sxs-lookup"><span data-stu-id="f2423-224">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="f2423-225">Metoda tworzy wystąpienia głównego agregacji, który jest miejscem docelowym bieżącego polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-225">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="f2423-226">Metoda jest wykonywana w wystąpieniu głównego agregacji, pobieranie danych wymagane polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-226">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="f2423-227">Istnieje nowy stan agregacji do jego bazie danych.</span><span class="sxs-lookup"><span data-stu-id="f2423-227">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="f2423-228">Ta ostatnia operacja jest rzeczywista transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2423-228">This last operation is the actual transaction.</span></span>

<span data-ttu-id="f2423-229">Zazwyczaj obsługi polecenia obsługuje pojedynczy agregacji, wynikają z głównym agregacji (jednostka głównego).</span><span class="sxs-lookup"><span data-stu-id="f2423-229">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="f2423-230">Jeśli Agreguje wiele powinny mieć wpływ na odebranie jednego polecenia, można za pomocą zdarzeń domeny propagowanie Agreguje wiele stanów lub akcji</span><span class="sxs-lookup"><span data-stu-id="f2423-230">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates</span></span>

<span data-ttu-id="f2423-231">Należy koniecznie zwrócić uwagę to, że podczas przetwarzania polecenia całą logikę domeny powinien znajdować się w modelu domeny (agregacji) pełni hermetyzowany i gotowa do przeprowadzania testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="f2423-231">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="f2423-232">Program obsługi poleceń po prostu działa jako sposób uzyskać modelu domeny z bazy danych i ostatni krok mówić warstwę infrastruktury (repozytoria), aby utrwalić zmiany po zmianie modelu.</span><span class="sxs-lookup"><span data-stu-id="f2423-232">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="f2423-233">Zaletą tej metody jest, że można Refaktoryzuj logika domeny w modelu domeny izolowanym, pełni hermetyzowany, rozbudowane, behawioralnej bez zmiany kodu w aplikacji lub infrastruktury warstw, które są poziom żmudne procesy (programy obsługi poleceń, interfejsu API sieci Web, repozytoria itp.).</span><span class="sxs-lookup"><span data-stu-id="f2423-233">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="f2423-234">Podczas obsługi polecenia uzyskać złożonych z logiką zbyt dużo, który może być zapachu kodu.</span><span class="sxs-lookup"><span data-stu-id="f2423-234">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="f2423-235">Przejrzyj je, a Jeśli znajdziesz logika domeny zrefaktoryzuj kod, aby przenieść tego zachowania domeny do metod obiektów domeny (łączny główna i podrzędna jednostka).</span><span class="sxs-lookup"><span data-stu-id="f2423-235">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="f2423-236">Na przykład klasa obsługi polecenia poniższy kod przedstawia tej samej klasy CreateOrderCommandHandler, który był wyświetlany na początku tego działu.</span><span class="sxs-lookup"><span data-stu-id="f2423-236">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="f2423-237">W takim przypadku firma Microsoft ma wyróżnione dojścia metody i operacje z obiektami modelu domeny/agregacji.</span><span class="sxs-lookup"><span data-stu-id="f2423-237">In this case we have highlighted the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

<span data-ttu-id="f2423-238">Program obsługi poleceń należy wykonać dodatkowe kroki, są to:</span><span class="sxs-lookup"><span data-stu-id="f2423-238">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="f2423-239">Użyj polecenia danych z metody i zachowanie elementu głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="f2423-239">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="f2423-240">Wewnętrznie w obiektach domeny wywołania domeny zdarzeń, gdy transakcja jest wykonywana, ale jest przezroczysty z punktu widzenia obsługi polecenia.</span><span class="sxs-lookup"><span data-stu-id="f2423-240">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="f2423-241">Jeśli wynik działania wartości zagregowanej zakończy się pomyślnie, a po zakończeniu transakcji, Wywołaj program obsługi poleceń zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="f2423-241">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="f2423-242">(Te mogą również być zgłaszany przez klas infrastruktury, takich jak repozytoriów.)</span><span class="sxs-lookup"><span data-stu-id="f2423-242">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f2423-243">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="f2423-243">Additional resources</span></span>

-   <span data-ttu-id="f2423-244">**Seemann znaku. Na granicach, aplikacje są zorientowane obiektowo nie**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, zorientowane na ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="f2423-244">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="f2423-245">**Poleceń i zdarzeń**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="f2423-245">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="f2423-246">**Do czego służy program obsługi polecenia? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="f2423-246">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="f2423-247">**Jimmy Bogard. Wzorce poleceń domeny — programy obsługi**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="f2423-247">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="f2423-248">**Jimmy Bogard. Wzorce poleceń domeny — Weryfikacja**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="f2423-248">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="f2423-249">Polecenie potoku proces: sposób włączania obsługi polecenia</span><span class="sxs-lookup"><span data-stu-id="f2423-249">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="f2423-250">Następne pytanie jest o wywoływaniu programem obsługi.</span><span class="sxs-lookup"><span data-stu-id="f2423-250">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="f2423-251">Można ręcznie wywołać ją z każdym pokrewne kontrolera ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f2423-251">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="f2423-252">Jednak metoda byłaby zbyt połączeniu i nie jest idealnym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="f2423-252">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="f2423-253">Inne dwa główne, które są zalecane opcje, są następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="f2423-253">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="f2423-254">Za pomocą wzorca artefaktu mediatora w pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2423-254">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="f2423-255">Z kolejki komunikatów asynchronicznych, Between kontrolerów i obsługi.</span><span class="sxs-lookup"><span data-stu-id="f2423-255">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="f2423-256">W potoku polecenia przy użyciu wzorca mediatora (w pamięci)</span><span class="sxs-lookup"><span data-stu-id="f2423-256">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="f2423-257">Jak pokazano w rysunek 9-21, w podejściu CQRS służy inteligentnego mediatora, podobnie jak magistrala w pamięci, czyli inteligentne przekierowywanie do obsługi polecenie right na podstawie typu polecenia lub DTO odbierane.</span><span class="sxs-lookup"><span data-stu-id="f2423-257">As shown in Figure 9-21, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="f2423-258">Pojedynczy czarne strzałki między składnikami reprezentują zależności między obiekty (w wielu przypadkach wprowadzonym za pośrednictwem Podpisane) z ich powiązane interakcje.</span><span class="sxs-lookup"><span data-stu-id="f2423-258">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="f2423-259">**Rysunek 9-21**.</span><span class="sxs-lookup"><span data-stu-id="f2423-259">**Figure 9-21**.</span></span> <span data-ttu-id="f2423-260">Przy użyciu wzorca mediatora w procesie w jednym mikrousługi CQRS</span><span class="sxs-lookup"><span data-stu-id="f2423-260">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="f2423-261">Pasującą przy użyciu wzorca mediatora dzieje się tak że w aplikacjach dla przedsiębiorstw, przetwarzania żądań można uzyskać skomplikowane.</span><span class="sxs-lookup"><span data-stu-id="f2423-261">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="f2423-262">Chcesz mieć możliwość dodawania Otwórz liczba kompleksowymi problemy, takie jak rejestrowanie, sprawdzanie poprawności, inspekcji i zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="f2423-262">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="f2423-263">W takich przypadkach polega na potoku mediatora (zobacz [wzorzec mediatora](https://en.wikipedia.org/wiki/Mediator_pattern)) do wymuszenia dla tych dodatkowych zachowania lub kompleksowymi problemy.</span><span class="sxs-lookup"><span data-stu-id="f2423-263">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="f2423-264">Obiekt hermetyzujący "jak" tego procesu jest mediatora: go koordynuje wykonywania na podstawie stanu, sposób obsługi polecenia jest wywoływana lub ładunku Podaj do programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="f2423-264">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="f2423-265">Ze składnikiem mediatora można zastosować kompleksowymi problemy w sposób scentralizowany i przejrzysty, stosując elementów decorator (lub [potoku zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) od mediatora v3).</span><span class="sxs-lookup"><span data-stu-id="f2423-265">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since Mediator v3).</span></span> <span data-ttu-id="f2423-266">(Aby uzyskać więcej informacji, zobacz [wzorzec Dekoratora](https://en.wikipedia.org/wiki/Decorator_pattern).)</span><span class="sxs-lookup"><span data-stu-id="f2423-266">(For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).)</span></span>

<span data-ttu-id="f2423-267">Elementy decorator i zachowania są podobne do [aspekt ukierunkowane programowania (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)tylko zastosowane do zarządzanych przez składnik mediatora potoku określonego procesu.</span><span class="sxs-lookup"><span data-stu-id="f2423-267">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="f2423-268">Aspektów AOP implementujących dotyczy kompleksowymi są stosowane na podstawie *weavers aspekt* wprowadzonym w czasie kompilacji lub w oparciu o przechwytywaniu wywołania obiektu.</span><span class="sxs-lookup"><span data-stu-id="f2423-268">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="f2423-269">Obu podejść typowe AOP czasami są określane jako działania "magic", ponieważ nie jest łatwo sprawdzić, jak AOP działa jej.</span><span class="sxs-lookup"><span data-stu-id="f2423-269">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="f2423-270">Podczas pracy nad poważnych problemów i zgłaszanie usterek, AOP może być trudne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="f2423-270">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="f2423-271">Z drugiej strony te elementy decorator/zachowania są jawne i stosowane tylko w kontekście mediatora, więc debugowanie jest bardziej przewidywalna i łatwe.</span><span class="sxs-lookup"><span data-stu-id="f2423-271">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="f2423-272">Na przykład w eShopOnContainers kolejności mikrousługi, wprowadziliśmy dwa dekoratory próbki, [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) klasy i [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) klasy.</span><span class="sxs-lookup"><span data-stu-id="f2423-272">For example, in the eShopOnContainers ordering microservice, we implemented two sample decorators, a [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class and a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class.</span></span> <span data-ttu-id="f2423-273">Implementacja dekoratora znajduje się w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="f2423-273">The decorator’s implementation is explained in the next section.</span></span> <span data-ttu-id="f2423-274">Należy pamiętać, że w przyszłych wersjach eShopOnContainers spowoduje zmigrowanie [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) i przejdź do [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) zamiast elementów decorator.</span><span class="sxs-lookup"><span data-stu-id="f2423-274">Note that in a future version, eShopOnContainers will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="f2423-275">W potoku do polecenia, używając kolejek wiadomości (poza procesem)</span><span class="sxs-lookup"><span data-stu-id="f2423-275">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="f2423-276">Wybór innego polega na użyciu asynchronicznej wiadomości na podstawie brokerzy lub kolejki komunikatów, jak pokazano w rysunek 9-22.</span><span class="sxs-lookup"><span data-stu-id="f2423-276">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-22.</span></span> <span data-ttu-id="f2423-277">Ta opcja również można łączyć ze składnikiem mediatora bezpośrednio poprzedzający program obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f2423-277">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="f2423-278">**Rysunek 9-22**.</span><span class="sxs-lookup"><span data-stu-id="f2423-278">**Figure 9-22**.</span></span> <span data-ttu-id="f2423-279">Za pomocą polecenia CQRS, używając kolejek wiadomości (poza procesem i komunikacji między procesami)</span><span class="sxs-lookup"><span data-stu-id="f2423-279">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="f2423-280">Za pomocą wiadomości kolejki, aby zaakceptować polecenia można bardziej szczegółowo skomplikować potoku dla polecenia, ponieważ prawdopodobnie będzie konieczne podzielić potok dwa procesy połączone za pośrednictwem kolejki wiadomości zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="f2423-280">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="f2423-281">Nadal należy używać, gdy trzeba mieć zwiększona skalowalność i wydajność w oparciu asynchroniczną obsługę wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f2423-281">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="f2423-282">Należy wziąć pod uwagę, że w przypadku rysunek 9-22 kontroler tylko zapisuje komunikat polecenia do kolejki i zwraca.</span><span class="sxs-lookup"><span data-stu-id="f2423-282">Consider that in the case of Figure 9-22, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="f2423-283">Następnie programy obsługi poleceń przetwarzanie wiadomości we własnym tempie.</span><span class="sxs-lookup"><span data-stu-id="f2423-283">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="f2423-284">Oznacza to doskonały korzyści kolejek — kolejki wiadomości może działać jako buforu w przypadkach gdy skalowalność funkcji hyper jest wymagane, takie jak w przypadku zasobów lub innych scenariuszy z dużą liczbę danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f2423-284">That is a great benefit of queues—the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="f2423-285">Jednak ze względu na asynchroniczne charakter kolejki komunikatów, należy dowiedzieć się, jak do komunikacji z aplikacją klient o powodzeniu lub niepowodzeniu polecenia procesu.</span><span class="sxs-lookup"><span data-stu-id="f2423-285">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="f2423-286">Zgodnie z zasadą nigdy nie należy używać poleceń "wyzwalać i zapomnij".</span><span class="sxs-lookup"><span data-stu-id="f2423-286">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="f2423-287">Każda aplikacja biznesowa musi wiedzieć, jeśli polecenie zostało przetworzone pomyślnie, co najmniej zweryfikowane i zaakceptowane.</span><span class="sxs-lookup"><span data-stu-id="f2423-287">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="f2423-288">W związku z tym możliwość odpowiedzi do klienta po weryfikacji komunikatem polecenia, który został przesłany do asynchronicznego kolejki dodaje złożoność do systemu, w porównaniu do polecenia w trakcie procesu, który zwraca wynik operacji po uruchomieniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="f2423-288">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="f2423-289">Korzystanie z kolejek, konieczne może być zwrócić wyników polecenia procesu za pomocą innych wiadomości wynik operacji, które będzie wymagać dodatkowych składników i niestandardowych komunikacji w systemie.</span><span class="sxs-lookup"><span data-stu-id="f2423-289">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="f2423-290">Ponadto polecenia asynchroniczne są jednokierunkowe poleceń, które w wielu przypadkach mogą nie być wymagane, opisane w poniższych interesujące wymiany między Burtsev Alexey i małych Gregowi w [online konwersacji](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="f2423-290">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="f2423-291">\[Burtsev Alexey\] znaleźć się części kodu, których użytkownicy korzystają Obsługa polecenia async lub jednokierunkowej polecenia wiadomości bez jakiegokolwiek powodu, aby to zrobić (nie robią niektórych długotrwałej operacji, nie są one wykonywanie kodu async zewnętrznych, ich nie nawet przechodzą aplikacji granic z magistrali komunikatów).</span><span class="sxs-lookup"><span data-stu-id="f2423-291">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="f2423-292">Dlaczego ich wprowadzenie tego niepotrzebnych złożoności?</span><span class="sxs-lookup"><span data-stu-id="f2423-292">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="f2423-293">I w rzeczywistości I nie zostało to jeszcze widoczne CQRS przykładowego kodu z blokuje programy obsługi poleceń wykonanej do tej pory, że będzie ona działać tak dobrze w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="f2423-293">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="f2423-294">\[Gregowi małych\] \[... \] asynchronicznej polecenie nie istnieje; jest faktycznie inne zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f2423-294">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="f2423-295">Jeśli musi zaakceptować, co możesz wysyłać mi i wywołaj zdarzenie, jeśli nie zgadzam się, nie jest już możesz informacją coś zrobić.</span><span class="sxs-lookup"><span data-stu-id="f2423-295">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="f2423-296">Jest możesz informujący, który coś zostało wykonane.</span><span class="sxs-lookup"><span data-stu-id="f2423-296">It's you telling me something has been done.</span></span> <span data-ttu-id="f2423-297">Prawdopodobnie to niewielka różnica na początku, ale ma wpływ na wiele.</span><span class="sxs-lookup"><span data-stu-id="f2423-297">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="f2423-298">Asynchroniczne polecenia znaczne zwiększenie złożoność systemu, ponieważ nie istnieje prosty sposób wskazująca błędów.</span><span class="sxs-lookup"><span data-stu-id="f2423-298">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="f2423-299">W związku z tym polecenia asynchroniczne nie są zalecane inne niż skalowania wymagania są potrzebne, lub w szczególnych przypadkach podczas komunikacji wewnętrznej mikrousług przy użyciu wiadomości.</span><span class="sxs-lookup"><span data-stu-id="f2423-299">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="f2423-300">W takich przypadkach należy projektować oddzielnego systemu raportowania i odzyskiwania na wypadek awarii.</span><span class="sxs-lookup"><span data-stu-id="f2423-300">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="f2423-301">W pierwotnej wersji eShopOnContainers zdecydowaliśmy się użyć polecenia synchronicznego przetwarzania, rozpoczynający się od żądań HTTP i regulowane przez wzorzec mediatora.</span><span class="sxs-lookup"><span data-stu-id="f2423-301">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="f2423-302">Które łatwo można zwrócić powodzenie lub niepowodzenie procesu, podobnie jak w [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementacji.</span><span class="sxs-lookup"><span data-stu-id="f2423-302">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="f2423-303">W każdym przypadku powinien to być decyzji na podstawie wymagań biznesowych w aplikacji lub w mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="f2423-303">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="f2423-304">Implementowanie potoku polecenie procesu z wzorcem mediatora (MediatR)</span><span class="sxs-lookup"><span data-stu-id="f2423-304">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="f2423-305">Jako przykładowe zastosowanie ten przewodnik przedstawia za pomocą potoku w procesie oparte na wzorcu mediatora na wprowadzanie polecenia dysku i routing, w pamięci, do obsługi polecenie right.</span><span class="sxs-lookup"><span data-stu-id="f2423-305">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and routing them, in memory, to the right command handlers.</span></span> <span data-ttu-id="f2423-306">Przewodnik proponuje, stosowanie elementów decorator lub [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) aby oddzielić kompleksowymi problemy.</span><span class="sxs-lookup"><span data-stu-id="f2423-306">The guide also proposes applying decorators or [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="f2423-307">Implementacja .NET Core są dostępne wielu bibliotekach open source, które implementują wzorzec mediatora.</span><span class="sxs-lookup"><span data-stu-id="f2423-307">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="f2423-308">Biblioteka używanych w tym przewodniku jest [MediatR](https://github.com/jbogard/MediatR) biblioteki open source (utworzony przez Jimmy Bogard), ale można użyć innej metody.</span><span class="sxs-lookup"><span data-stu-id="f2423-308">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="f2423-309">MediatR jest niewielki i prosty biblioteki, która służy do przetwarzania komunikatów w pamięci, takich jak polecenia, podczas stosowania elementów decorator lub zachowania.</span><span class="sxs-lookup"><span data-stu-id="f2423-309">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="f2423-310">Przy użyciu wzorca mediatora pomaga ograniczyć sprzężenia i do izolowania problemów żądanej pracy, podczas łączenia automatycznie do programu obsługi, który wykonuje pracy — w takim przypadku na programy obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f2423-310">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="f2423-311">Kolejny powód dobra do użycia z wzorcem mediatora wyjaśniono przez Jimmy Bogard podczas przeglądania w tym przewodniku:</span><span class="sxs-lookup"><span data-stu-id="f2423-311">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="f2423-312">Myślę, może być warto zauważyć testowania w tym miejscu — zapewnia nieuprzywilejowany zgodne okno do zachowania systemu.</span><span class="sxs-lookup"><span data-stu-id="f2423-312">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="f2423-313">W żądaniu, poza odpowiedzi. Znaleziono element bardzo przydatna w budynku spójnie zachowuje testy.</span><span class="sxs-lookup"><span data-stu-id="f2423-313">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="f2423-314">Najpierw Daj nam zapoznaj się z kodem kontroler faktycznie użycia obiektu mediatora.</span><span class="sxs-lookup"><span data-stu-id="f2423-314">First, let us take a look to the controller code where you actually would use the mediator object.</span></span> <span data-ttu-id="f2423-315">Obiekt mediatora nie były używane, należy wprowadzić wszystkie zależności dla tego kontrolera, np. obiekt rejestratora i inne.</span><span class="sxs-lookup"><span data-stu-id="f2423-315">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="f2423-316">W związku z tym Konstruktor jest dość złożone.</span><span class="sxs-lookup"><span data-stu-id="f2423-316">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="f2423-317">Z drugiej strony Jeśli używasz obiektu mediatora konstruktora kontroler może być znacznie prostsze, kilka zależności, zamiast wiele zależności, które byłyby gdyby jeden na operację kompleksowymi, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f2423-317">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies that you would have if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

<span data-ttu-id="f2423-318">Widać, że mediatora zapewnia czyste i gotowa konstruktora kontrolera interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="f2423-318">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="f2423-319">Ponadto w ramach metod kontrolera kod, aby wysyłać polecenia do obiektu mediatora jest prawie jeden wiersz:</span><span class="sxs-lookup"><span data-stu-id="f2423-319">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

<span data-ttu-id="f2423-320">MediatR pod uwagę klasy obsługi polecenia, należy zarejestrować klasy mediatora i klasy programu obsługi poleceń w Twojej kontenera IoC.</span><span class="sxs-lookup"><span data-stu-id="f2423-320">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="f2423-321">Domyślnie MediatR używa Autofac jako kontenera IoC, ale można również użyć wbudowanych kontenera ASP.NET Core IoC lub innych kontenera obsługiwane przez MediatR.</span><span class="sxs-lookup"><span data-stu-id="f2423-321">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="f2423-322">Poniższy kod przedstawia sposób rejestrowania poleceń i typów w mediatora przy użyciu modułów Autofac.</span><span class="sxs-lookup"><span data-stu-id="f2423-322">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

<span data-ttu-id="f2423-323">Ponieważ każdy program obsługi poleceń implementuje interfejs z ogólnym IAsyncRequestHandler&lt;T&gt; , a następnie sprawdza RegisteredAssemblyTypes obiektu, program obsługi jest w stanie powiązać każde polecenie z programem obsługi, ponieważ który określona relacja commandhandler — obiekt klasy, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="f2423-323">Because each command handler implements the interface with generic IAsyncRequestHandler&lt;T&gt; and then inspects the RegisteredAssemblyTypes object, the handler is able to relate each command with its command handler, because that relationship is stated in the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="f2423-324">To jest kod odpowiadająca poleceń z programy obsługi poleceń.</span><span class="sxs-lookup"><span data-stu-id="f2423-324">This is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="f2423-325">Program obsługi ma prostą klasę, ale dziedziczy on z RequestHandler&lt;T&gt;, i MediatR zapewnia on wywołany z poprawną ładunku.</span><span class="sxs-lookup"><span data-stu-id="f2423-325">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it gets invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a><span data-ttu-id="f2423-326">Stosowanie kompleksowymi problemy podczas przetwarzania polecenia wzorami mediatora i Dekoratora</span><span class="sxs-lookup"><span data-stu-id="f2423-326">Applying cross-cutting concerns when processing commands with the Mediator and Decorator patterns</span></span>

<span data-ttu-id="f2423-327">Istnieje więcej rzecz: możliwość dotyczą problemów kompleksowymi mediatora potoku.</span><span class="sxs-lookup"><span data-stu-id="f2423-327">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="f2423-328">Możesz również sprawdzić w końcu kod modułu rejestracji Autofac jak jest rejestrowanie dekoratora typ, w szczególności niestandardowej klasy LogDecorator.</span><span class="sxs-lookup"><span data-stu-id="f2423-328">You can also see at the end of the Autofac registration module code how it is registering a decorator type, specifically, a custom LogDecorator class.</span></span>

<span data-ttu-id="f2423-329">Ponownie, należy pamiętać, że przyszłej wersji eShopOnContainers go spowoduje zmigrowanie [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) i przejdź do [zachowania](https://github.com/jbogard/MediatR/wiki/Behaviors) zamiast elementów decorator.</span><span class="sxs-lookup"><span data-stu-id="f2423-329">Again, note that a future version of eShopOnContainers it will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

<span data-ttu-id="f2423-330">Czy [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) jako następujący kod, który rejestruje informacje na temat program obsługi poleceń, które było wykonywane, i czy było pomyślne lub nie można zaimplementować klasy.</span><span class="sxs-lookup"><span data-stu-id="f2423-330">That [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

<span data-ttu-id="f2423-331">Wystarczy implementowania tej klasy dekoratora i przez potok wraz z jego dekoracji wszystkich poleceń, które są przetwarzane przez MediatR będzie rejestrowanie informacji na temat wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f2423-331">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="f2423-332">EShopOnContainers porządkowanie mikrousługi ma zastosowanie również w drugim dekoratora dla podstawowych operacji sprawdzania poprawności, [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) klasy, która zależy od [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, jak pokazano w następujący kod:</span><span class="sxs-lookup"><span data-stu-id="f2423-332">The eShopOnContainers ordering microservice also applies a second decorator for basic validations, the [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

<span data-ttu-id="f2423-333">Następnie, na podstawie [FluentValidation](https://github.com/JeremySkinner/FluentValidation) biblioteki, utworzyliśmy sprawdzanie poprawności danych przekazanych z CreateOrderCommand, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="f2423-333">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}
```

<span data-ttu-id="f2423-334">Można utworzyć dodatkowe operacje sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f2423-334">You could create additional validations.</span></span> <span data-ttu-id="f2423-335">Jest to bardzo czyste i elegancki sposób implementacji Twojego polecenia operacji sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="f2423-335">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="f2423-336">W podobny sposób można zaimplementować innych elementów decorator dodatkowe aspekty lub kompleksowymi problemy, które mają być stosowane do poleceń podczas ich obsługę.</span><span class="sxs-lookup"><span data-stu-id="f2423-336">In a similar way, you could implement other decorators for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="f2423-337">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="f2423-337">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="f2423-338">Wzorzec mediatora</span><span class="sxs-lookup"><span data-stu-id="f2423-338">The mediator pattern</span></span>

-   <span data-ttu-id="f2423-339">**Wzorzec mediatora**
    [*https://en.wikipedia.org/wiki/Mediator\_wzorca*](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="f2423-339">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="f2423-340">Wzorzec dekoratora</span><span class="sxs-lookup"><span data-stu-id="f2423-340">The decorator pattern</span></span>

-   <span data-ttu-id="f2423-341">**Wzorzec dekoratora**
    [*https://en.wikipedia.org/wiki/Decorator\_wzorca*](https://en.wikipedia.org/wiki/Decorator_pattern)</span><span class="sxs-lookup"><span data-stu-id="f2423-341">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="f2423-342">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="f2423-342">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="f2423-343">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="f2423-343">**MediatR.**</span></span> <span data-ttu-id="f2423-344">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f2423-344">GitHub repo.</span></span>
    [<span data-ttu-id="f2423-345">*https://github.com/jbogard/MediatR*</span><span class="sxs-lookup"><span data-stu-id="f2423-345">*https://github.com/jbogard/MediatR*</span></span>](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="f2423-346">**CQRS MediatR i AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="f2423-346">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="f2423-347">**Umieść kontrolerów tradycyjną: ogłoszeń i poleceń. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="f2423-347">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="f2423-348">**Poruszając kompleksowymi problemy z potokiem mediatora**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="f2423-348">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="f2423-349">**CQRS i REST: czego szukasz**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="f2423-349">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="f2423-350">**Przykłady potoku MediatR**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="f2423-350">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="f2423-351">**Wycinek pionowy testów osprzętu MediatR i ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*</span><span class="sxs-lookup"><span data-stu-id="f2423-351">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="f2423-352">**Rozszerzenia MediatR iniekcji zależności Microsoft wydała**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="f2423-352">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="f2423-353">Sprawdzanie poprawności Fluent</span><span class="sxs-lookup"><span data-stu-id="f2423-353">Fluent validation</span></span>

-   <span data-ttu-id="f2423-354">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="f2423-354">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="f2423-355">Repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f2423-355">GitHub repo.</span></span>
    [<span data-ttu-id="f2423-356">*https://github.com/JeremySkinner/FluentValidation*</span><span class="sxs-lookup"><span data-stu-id="f2423-356">*https://github.com/JeremySkinner/FluentValidation*</span></span>](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="f2423-357">[Poprzednie] (microservice-application-layer-web-api-design.md) [dalej] (.. /Implement-resilient-Applications/index.MD)</span><span class="sxs-lookup"><span data-stu-id="f2423-357">[Previous] (microservice-application-layer-web-api-design.md) [Next] (../implement-resilient-applications/index.md)</span></span>
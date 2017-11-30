---
title: "Jaki &#39; s Nowość w wersji WPF 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Presentation Foundation [WPF], what's new
- WPF [WPF], what's new
ms.assetid: db086ae4-70bb-4862-95db-2eaca5216bc3
caps.latest.revision: "55"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4dc6a35a0ff8586b91ab7d74abc182fa6002f88
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/11/2017
---
# <a name="what39s-new-in-wpf-version-45"></a><span data-ttu-id="fed02-102">Jaki &#39; s Nowość w wersji WPF 4.5</span><span class="sxs-lookup"><span data-stu-id="fed02-102">What&#39;s New in WPF Version 4.5</span></span>
<span data-ttu-id="fed02-103"><a name="introduction"></a>Ten temat zawiera informacje o nowych i ulepszonych funkcjach [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] wersji 4.5.</span><span class="sxs-lookup"><span data-stu-id="fed02-103"><a name="introduction"></a> This topic contains information about new and enhanced features in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] version 4.5.</span></span>  
  
 <span data-ttu-id="fed02-104">Ten temat zawiera następujące sekcje:</span><span class="sxs-lookup"><span data-stu-id="fed02-104">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="fed02-105">Formant wstążki</span><span class="sxs-lookup"><span data-stu-id="fed02-105">Ribbon control</span></span>](#ribbon_control)  
  
-   [<span data-ttu-id="fed02-106">Zwiększona wydajność podczas wyświetlania dużych zestawów danych grupowanych</span><span class="sxs-lookup"><span data-stu-id="fed02-106">Improved performance when displaying large sets of grouped data</span></span>](#grouped_virtualization)  
  
-   [<span data-ttu-id="fed02-107">Nowe funkcje VirtualizingPanel</span><span class="sxs-lookup"><span data-stu-id="fed02-107">New features for the VirtualizingPanel</span></span>](#VirtualizingPanel)  
  
-   [<span data-ttu-id="fed02-108">Powiązanie z właściwości statyczne</span><span class="sxs-lookup"><span data-stu-id="fed02-108">Binding to static properties</span></span>](#static_properties)  
  
-   [<span data-ttu-id="fed02-109">Uzyskiwanie dostępu do kolekcji na wątków bez interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fed02-109">Accessing collections on non-UI Threads</span></span>](#xthread_access)  
  
-   [<span data-ttu-id="fed02-110">Synchronicznego i asynchronicznego sprawdzanie poprawności danych</span><span class="sxs-lookup"><span data-stu-id="fed02-110">Synchronously and Asynchronously validating data</span></span>](#INotifyDataErrorInfo)  
  
-   [<span data-ttu-id="fed02-111">Automatyczne aktualizowanie źródła powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="fed02-111">Automatically updating the source of a data binding</span></span>](#delay)  
  
-   [<span data-ttu-id="fed02-112">Powiązanie z typów tej ICustomTypeProvider wdrożenie</span><span class="sxs-lookup"><span data-stu-id="fed02-112">Binding to types that Implement ICustomTypeProvider</span></span>](#ICustomTypeProvider)  
  
-   [<span data-ttu-id="fed02-113">Pobieranie informacje o powiązaniu danych z wyrażenia powiązania</span><span class="sxs-lookup"><span data-stu-id="fed02-113">Retrieving data binding information from a binding expression</span></span>](#binding_state)  
  
-   [<span data-ttu-id="fed02-114">Sprawdzanie, czy prawidłowy obiekt DataContext</span><span class="sxs-lookup"><span data-stu-id="fed02-114">Checking for a valid DataContext object</span></span>](#DisconnectedSource)  
  
-   [<span data-ttu-id="fed02-115">Zmienianie położenia danych po zmianie wartości danych (kształtowania na żywo)</span><span class="sxs-lookup"><span data-stu-id="fed02-115">Repositioning data as the data's values change (Live shaping)</span></span>](#live_shaping)  
  
-   [<span data-ttu-id="fed02-116">Ulepszona obsługa ustanawianie słabe odwołanie do zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fed02-116">Improved Support for Establishing a Weak Reference to an Event</span></span>](#weak_event_pattern)  
  
-   [<span data-ttu-id="fed02-117">Nowe metody dla klasy dyspozytora</span><span class="sxs-lookup"><span data-stu-id="fed02-117">New methods for the Dispatcher class</span></span>](#async)  
  
-   [<span data-ttu-id="fed02-118">Rozszerzenia znaczników dla zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fed02-118">Markup Extensions for Events</span></span>](#events_markup_extenions)  
  
<a name="ribbon_control"></a>   
## <a name="ribbon-control"></a><span data-ttu-id="fed02-119">Formant wstążki</span><span class="sxs-lookup"><span data-stu-id="fed02-119">Ribbon control</span></span>  
 <span data-ttu-id="fed02-120">WPF 4.5 jest dostarczany z <xref:System.Windows.Controls.Ribbon.Ribbon> formant, który obsługuje kart, aplikacji Menu i paska narzędzi Szybki dostęp.</span><span class="sxs-lookup"><span data-stu-id="fed02-120">WPF 4.5 ships with a <xref:System.Windows.Controls.Ribbon.Ribbon> control that hosts a Quick Access Toolbar, Application Menu, and tabs.</span></span>  <span data-ttu-id="fed02-121">Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](/visualstudio/vsto/ribbon-overview).</span><span class="sxs-lookup"><span data-stu-id="fed02-121">For more information, see the [Ribbon Overview](/visualstudio/vsto/ribbon-overview).</span></span>  
  
<a name="grouped_virtualization"></a>   
## <a name="improved-performance-when-displaying-large-sets-of-grouped-data"></a><span data-ttu-id="fed02-122">Zwiększona wydajność podczas wyświetlania dużych zestawów danych grupowanych</span><span class="sxs-lookup"><span data-stu-id="fed02-122">Improved performance when displaying large sets of grouped data</span></span>  
 <span data-ttu-id="fed02-123">Wirtualizacji interfejsu użytkownika występuje, gdy podzestaw interfejsu użytkownika (UI) elementy zostaną wygenerowane na podstawie większą liczbę elementów danych oparte na elementy, które są widoczne na ekranie.</span><span class="sxs-lookup"><span data-stu-id="fed02-123">UI virtualization occurs when  a subset of user interface (UI) elements are generated from a larger number of data items based on which items are visible on the screen.</span></span> <span data-ttu-id="fed02-124"><xref:System.Windows.Controls.VirtualizingPanel> Definiuje <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dołączona właściwość, która umożliwia wirtualizacji interfejsu użytkownika dla zgrupowanych danych.</span><span class="sxs-lookup"><span data-stu-id="fed02-124">The <xref:System.Windows.Controls.VirtualizingPanel> defines the <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> attached property that enables UI Virtualization for grouped data.</span></span>  <span data-ttu-id="fed02-125">Aby uzyskać więcej informacji na temat grupowania danych, zobacz porady: sortowanie i grupy danych przy użyciu widoku w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="fed02-125">For more information about grouping data, see How to: Sort and Group Data Using a View in XAML.</span></span>  <span data-ttu-id="fed02-126">Aby uzyskać więcej informacji na temat wirtualizacji pogrupowanych danych, zobacz <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="fed02-126">For more information about virtualizing grouped data, see the <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizingWhenGrouping%2A> attached property.</span></span>  
  
<a name="VirtualizingPanel"></a>   
## <a name="new-features-for-the-virtualizingpanel"></a><span data-ttu-id="fed02-127">Nowe funkcje VirtualizingPanel</span><span class="sxs-lookup"><span data-stu-id="fed02-127">New features for the VirtualizingPanel</span></span>  
  
1.  <span data-ttu-id="fed02-128">Można określić czy <xref:System.Windows.Controls.VirtualizingPanel>, takich jak <xref:System.Windows.Controls.VirtualizingStackPanel>, wyświetla elementy częściowe za pomocą <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="fed02-128">You can specify whether a <xref:System.Windows.Controls.VirtualizingPanel>, such as the <xref:System.Windows.Controls.VirtualizingStackPanel>, displays partial items by using the <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> attached property.</span></span> <span data-ttu-id="fed02-129">Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ustawiono <xref:System.Windows.Controls.ScrollUnit.Item>, <xref:System.Windows.Controls.VirtualizingPanel> będą wyświetlane tylko elementy, które są całkowicie widoczne.</span><span class="sxs-lookup"><span data-stu-id="fed02-129">If <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> is set to <xref:System.Windows.Controls.ScrollUnit.Item>, the <xref:System.Windows.Controls.VirtualizingPanel> will only display items that are completely visible.</span></span> <span data-ttu-id="fed02-130">Jeśli <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> ustawiono <xref:System.Windows.Controls.ScrollUnit.Pixel>, <xref:System.Windows.Controls.VirtualizingPanel> można wyświetlić częściowo widocznych elementów.</span><span class="sxs-lookup"><span data-stu-id="fed02-130">If <xref:System.Windows.Controls.VirtualizingPanel.ScrollUnit%2A> is set to <xref:System.Windows.Controls.ScrollUnit.Pixel>, the <xref:System.Windows.Controls.VirtualizingPanel> can display partially visible items.</span></span>  
  
2.  <span data-ttu-id="fed02-131">Można określić rozmiar pamięci podręcznej przed i po okienka ekranu po <xref:System.Windows.Controls.VirtualizingPanel> jest wirtualizacji za pomocą <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> dołączona właściwość.</span><span class="sxs-lookup"><span data-stu-id="fed02-131">You can specify the  size of the cache before and after the viewport when the <xref:System.Windows.Controls.VirtualizingPanel> is virtualizing by using the <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A> attached property.</span></span>  <span data-ttu-id="fed02-132">Pamięć podręczna jest ilość miejsca powyżej lub poniżej okienka ekranu, w którym nie są zwirtualizowane elementy.</span><span class="sxs-lookup"><span data-stu-id="fed02-132">The cache is the amount of space above or below the viewport in which items are not virtualized.</span></span>  <span data-ttu-id="fed02-133">Aby uniknąć generowania elementy interfejsu użytkownika, ponieważ są one przewijane w widoku przy użyciu pamięci podręcznej może poprawić wydajność.</span><span class="sxs-lookup"><span data-stu-id="fed02-133">Using a cache to avoid generating UI elements as they’re scrolled into view can improve performance.</span></span> <span data-ttu-id="fed02-134">Pamięci podręcznej jest wypełniana z niższym priorytetem, dzięki czemu aplikacja nie przestała odpowiadać podczas operacji.</span><span class="sxs-lookup"><span data-stu-id="fed02-134">The cache is populated at a lower priority so that the application does not become unresponsive during the operation.</span></span> <span data-ttu-id="fed02-135"><xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> Właściwość określa jednostki miary, która jest używana przez <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fed02-135">The <xref:System.Windows.Controls.VirtualizingPanel.CacheLengthUnit%2A?displayProperty=nameWithType> property determines the unit of measurement that is used by <xref:System.Windows.Controls.VirtualizingPanel.CacheLength%2A?displayProperty=nameWithType>.</span></span>  
  
<a name="static_properties"></a>   
## <a name="binding-to-static-properties"></a><span data-ttu-id="fed02-136">Powiązanie z właściwości statyczne</span><span class="sxs-lookup"><span data-stu-id="fed02-136">Binding to static properties</span></span>  
 <span data-ttu-id="fed02-137">Właściwości statyczne można użyć jako źródła danych powiązania.</span><span class="sxs-lookup"><span data-stu-id="fed02-137">You can use static properties as the source of a data binding.</span></span> <span data-ttu-id="fed02-138">Aparat wiązania danych rozpoznaje, gdy wartość właściwości Jeśli statyczne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fed02-138">The data binding engine recognizes when the property's value changes if a static event is raised.</span></span>  <span data-ttu-id="fed02-139">Na przykład jeśli klasa `SomeClass` definiuje właściwości statycznej o nazwie `MyProperty`, `SomeClass` można zdefiniować statyczne zdarzenie, które jest wywoływane, gdy wartość `MyProperty` zmiany.</span><span class="sxs-lookup"><span data-stu-id="fed02-139">For example, if the class `SomeClass` defines a static property called `MyProperty`, `SomeClass` can define a static event that is raised when the value of `MyProperty` changes.</span></span>  <span data-ttu-id="fed02-140">Zdarzenia statyczne można użyć jednej z następujących podpisów.</span><span class="sxs-lookup"><span data-stu-id="fed02-140">The static event can use either of the following signatures.</span></span>  
  
-   `public static event EventHandler MyPropertyChanged;`  
  
-   `public static event EventHandler<PropertyChangedEventArgs> StaticPropertyChanged;`  
  
 <span data-ttu-id="fed02-141">Uwaga w pierwszym przypadku klasa przedstawia zdarzenia statycznej o nazwie *PropertyName* `Changed` , który przekazuje <xref:System.EventArgs> do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fed02-141">Note that in the first case, the class exposes a static event named *PropertyName*`Changed` that passes <xref:System.EventArgs> to the event handler.</span></span>  <span data-ttu-id="fed02-142">W drugim przypadku klasa przedstawia zdarzenia statycznej o nazwie `StaticPropertyChanged` , który przekazuje <xref:System.ComponentModel.PropertyChangedEventArgs> do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fed02-142">In the second case, the class exposes a static event named `StaticPropertyChanged` that passes <xref:System.ComponentModel.PropertyChangedEventArgs> to the event handler.</span></span> <span data-ttu-id="fed02-143">Klasa, która implementuje statycznej właściwości można podnieść powiadomień zmiany właściwości przy użyciu jednej z metod.</span><span class="sxs-lookup"><span data-stu-id="fed02-143">A class that implements the static property can choose to raise property-change notifications using either method.</span></span>  
  
<a name="xthread_access"></a>   
## <a name="accessing-collections-on-non-ui-threads"></a><span data-ttu-id="fed02-144">Uzyskiwanie dostępu do kolekcji na wątków bez interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fed02-144">Accessing collections on non-UI Threads</span></span>  
 <span data-ttu-id="fed02-145">WPF umożliwia zbierania danych w wątkach innego niż utworzony kolekcji modyfikacji i dostępu.</span><span class="sxs-lookup"><span data-stu-id="fed02-145">WPF enables you to access and modify data collections on threads other than the one that created the collection.</span></span>  <span data-ttu-id="fed02-146">Pozwala na użycie wątku w tle, aby odbierać dane ze źródła zewnętrznego, takie jak bazy danych i wyświetlić dane w wątku interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fed02-146">This enables you to use a background thread to receive data from an external source, such as a database, and display the data on the UI thread.</span></span>  <span data-ttu-id="fed02-147">Za pomocą inny wątek, aby zmodyfikować kolekcję, do interakcji z użytkownikiem reaguje interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fed02-147">By using another thread to modify the collection, your user interface remains responsive to user interaction.</span></span>  
  
<a name="INotifyDataErrorInfo"></a>   
## <a name="synchronously-and-asynchronously-validating-data"></a><span data-ttu-id="fed02-148">Synchronicznego i asynchronicznego sprawdzanie poprawności danych</span><span class="sxs-lookup"><span data-stu-id="fed02-148">Synchronously and Asynchronously validating data</span></span>  
 <span data-ttu-id="fed02-149"><xref:System.ComponentModel.INotifyDataErrorInfo> Interfejs umożliwia klas jednostek danych do wdrożenia niestandardowych reguł walidacji i ujawnia asynchronicznie wyniki sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="fed02-149">The <xref:System.ComponentModel.INotifyDataErrorInfo> interface enables data entity classes to implement custom validation rules and expose validation results asynchronously.</span></span> <span data-ttu-id="fed02-150">Ten interfejs obsługuje również błędów niestandardowych obiektów, wiele błędów według właściwości, właściwość między błędy i błędy na poziomie jednostki.</span><span class="sxs-lookup"><span data-stu-id="fed02-150">This interface also supports custom error objects, multiple errors per property, cross-property errors, and entity-level errors.</span></span>  <span data-ttu-id="fed02-151">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.INotifyDataErrorInfo>.</span><span class="sxs-lookup"><span data-stu-id="fed02-151">For more information, see <xref:System.ComponentModel.INotifyDataErrorInfo>.</span></span>  
  
<a name="delay"></a>   
## <a name="automatically-updating-the-source-of-a-data-binding"></a><span data-ttu-id="fed02-152">Automatyczne aktualizowanie źródła powiązanie danych</span><span class="sxs-lookup"><span data-stu-id="fed02-152">Automatically updating the source of a data binding</span></span>  
 <span data-ttu-id="fed02-153">Jeśli używasz wiązanie danych do aktualizowania źródła danych, możesz użyć <xref:System.Windows.Data.BindingBase.Delay%2A> właściwość, aby określić ilość czasu, aby przekazać po zmianie właściwości w elemencie docelowym przed aktualizacji źródła.</span><span class="sxs-lookup"><span data-stu-id="fed02-153">If you use a data binding to update a data source, you can use the <xref:System.Windows.Data.BindingBase.Delay%2A> property to specify an amount of time to pass after the property changes on the target before the source updates.</span></span>  <span data-ttu-id="fed02-154">Na przykład, załóżmy, że masz <xref:System.Windows.Controls.Slider> mający jego <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> dwukierunkowe danych właściwości powiązany z właściwości obiektu danych i <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> właściwość jest ustawiona na <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span><span class="sxs-lookup"><span data-stu-id="fed02-154">For example, suppose that you have a <xref:System.Windows.Controls.Slider> that has its <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> property data two-way bound to a property of a data object and the <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> property is set to <xref:System.Windows.Data.UpdateSourceTrigger.PropertyChanged>.</span></span>  <span data-ttu-id="fed02-155">W tym przykładzie, gdy użytkownik przesuwa <xref:System.Windows.Controls.Slider>, aktualizacje źródła dla każdego piksela który <xref:System.Windows.Controls.Slider> przenosi.</span><span class="sxs-lookup"><span data-stu-id="fed02-155">In this example, when the user moves the <xref:System.Windows.Controls.Slider>, the source updates for each pixel that the <xref:System.Windows.Controls.Slider> moves.</span></span>  <span data-ttu-id="fed02-156">Obiekt źródłowy potrzebuje zazwyczaj wartość suwaka tylko wtedy, gdy suwak <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> zatrzymuje zmiana.</span><span class="sxs-lookup"><span data-stu-id="fed02-156">The source object typically needs the value of the slider only when the slider's <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> stops changing.</span></span>  <span data-ttu-id="fed02-157">Aby zapobiec zbyt często aktualizowanie źródła, użyj <xref:System.Windows.Data.BindingBase.Delay%2A> do określenia, czy źródło nie powinny być aktualizowane, dopóki nie upłynie określoną ilość czasu po stronie przycisku suwaka zatrzymuje przenoszenia.</span><span class="sxs-lookup"><span data-stu-id="fed02-157">To prevent updating the source too often, use <xref:System.Windows.Data.BindingBase.Delay%2A> to specify that the source should not be updated until a certain amount of time elapses after the thumb stops moving.</span></span>  
  
<a name="ICustomTypeProvider"></a>   
## <a name="binding-to-types-that-implement-icustomtypeprovider"></a><span data-ttu-id="fed02-158">Powiązanie z typów tej ICustomTypeProvider wdrożenie</span><span class="sxs-lookup"><span data-stu-id="fed02-158">Binding to types that Implement ICustomTypeProvider</span></span>  
 <span data-ttu-id="fed02-159">WPF obsługuje powiązanie danych do obiektów, które implementują <xref:System.Reflection.ICustomTypeProvider>, znanej również jako typów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fed02-159">WPF supports data binding to objects that implement <xref:System.Reflection.ICustomTypeProvider>, also known as custom types.</span></span>  <span data-ttu-id="fed02-160">Niestandardowych typów można używać w następujących przypadkach.</span><span class="sxs-lookup"><span data-stu-id="fed02-160">You can use custom types in the following cases.</span></span>  
  
1.  <span data-ttu-id="fed02-161">Jako <xref:System.Windows.PropertyPath> w powiązaniu danych.</span><span class="sxs-lookup"><span data-stu-id="fed02-161">As a <xref:System.Windows.PropertyPath> in a data binding.</span></span> <span data-ttu-id="fed02-162">Na przykład <xref:System.Windows.Data.Binding.Path%2A> właściwość <xref:System.Windows.Data.Binding> może odwoływać się właściwość typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="fed02-162">For example, the <xref:System.Windows.Data.Binding.Path%2A> property of a <xref:System.Windows.Data.Binding> can reference a property of a custom type.</span></span>  
  
2.  <span data-ttu-id="fed02-163">Jako wartość <xref:System.Windows.DataTemplate.DataType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fed02-163">As the value of the <xref:System.Windows.DataTemplate.DataType%2A> property.</span></span>  
  
3.  <span data-ttu-id="fed02-164">Typem, który określa automatycznie generowanych kolumn w <xref:System.Windows.Controls.DataGrid>.</span><span class="sxs-lookup"><span data-stu-id="fed02-164">As a type that determines the automatically generated columns in a <xref:System.Windows.Controls.DataGrid>.</span></span>  
  
<a name="binding_state"></a>   
## <a name="retrieving-data-binding-information-from-a-binding-expression"></a><span data-ttu-id="fed02-165">Pobieranie informacje o powiązaniu danych z wyrażenia powiązania</span><span class="sxs-lookup"><span data-stu-id="fed02-165">Retrieving data binding information from a binding expression</span></span>  
 <span data-ttu-id="fed02-166">W niektórych przypadkach może uzyskać <xref:System.Windows.Data.BindingExpression> z <xref:System.Windows.Data.Binding> i potrzebują informacji dotyczących obiektu źródłowego i docelowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fed02-166">In certain cases, you might get the <xref:System.Windows.Data.BindingExpression> of a <xref:System.Windows.Data.Binding> and need information about the source and target objects of the binding.</span></span>  <span data-ttu-id="fed02-167">Umożliwiają uzyskanie źródłowy lub docelowy obiekt lub właściwości skojarzonej, ponieważ zostały dodane nowe interfejsy API.</span><span class="sxs-lookup"><span data-stu-id="fed02-167">New APIs have been added to enable you to get the source or target object or the associated property.</span></span>  <span data-ttu-id="fed02-168">Jeśli masz <xref:System.Windows.Data.BindingExpression>, użyj następujących interfejsów API, aby uzyskać informacje o źródłowe i docelowe.</span><span class="sxs-lookup"><span data-stu-id="fed02-168">When you have a <xref:System.Windows.Data.BindingExpression>, use the following APIs to get information about the target and source.</span></span>  
  
|<span data-ttu-id="fed02-169">Aby znaleźć tę wartość powiązania</span><span class="sxs-lookup"><span data-stu-id="fed02-169">To find this value of the binding</span></span>|<span data-ttu-id="fed02-170">Użyj tego interfejsu API</span><span class="sxs-lookup"><span data-stu-id="fed02-170">Use this API</span></span>|  
|---------------------------------------|------------------|  
|<span data-ttu-id="fed02-171">Obiekt docelowy</span><span class="sxs-lookup"><span data-stu-id="fed02-171">The target object</span></span>|<xref:System.Windows.Data.BindingExpressionBase.Target%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fed02-172">Właściwość target</span><span class="sxs-lookup"><span data-stu-id="fed02-172">The target property</span></span>|<xref:System.Windows.Data.BindingExpressionBase.TargetProperty%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fed02-173">Obiekt źródłowy</span><span class="sxs-lookup"><span data-stu-id="fed02-173">The source object</span></span>|<xref:System.Windows.Data.BindingExpression.ResolvedSource%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fed02-174">Właściwość źródła</span><span class="sxs-lookup"><span data-stu-id="fed02-174">The source property</span></span>|<xref:System.Windows.Data.BindingExpression.ResolvedSourcePropertyName%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fed02-175">Czy <xref:System.Windows.Data.BindingExpression> należy do<xref:System.Windows.Data.BindingGroup></span><span class="sxs-lookup"><span data-stu-id="fed02-175">Whether the <xref:System.Windows.Data.BindingExpression> belongs to a <xref:System.Windows.Data.BindingGroup></span></span>|<xref:System.Windows.Data.BindingExpressionBase.BindingGroup%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="fed02-176">Właściciel<xref:System.Windows.Data.BindingGroup></span><span class="sxs-lookup"><span data-stu-id="fed02-176">The owner of a <xref:System.Windows.Data.BindingGroup></span></span>|<xref:System.Windows.Data.BindingGroup.Owner%2A>|  
  
<a name="DisconnectedSource"></a>   
## <a name="checking-for-a-valid-datacontext-object"></a><span data-ttu-id="fed02-177">Sprawdzanie, czy prawidłowy obiekt DataContext</span><span class="sxs-lookup"><span data-stu-id="fed02-177">Checking for a valid DataContext object</span></span>  
 <span data-ttu-id="fed02-178">Istnieją przypadki, gdzie <xref:System.Windows.FrameworkElement.DataContext%2A> elementu kontenera w <xref:System.Windows.Controls.ItemsControl> zostanie rozłączony.</span><span class="sxs-lookup"><span data-stu-id="fed02-178">There are cases where the <xref:System.Windows.FrameworkElement.DataContext%2A> of an item container in an <xref:System.Windows.Controls.ItemsControl> becomes disconnected.</span></span>  <span data-ttu-id="fed02-179">Kontener elementu jest element interfejsu użytkownika, który zawiera element <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="fed02-179">An item container is the UI element that displays an item in an <xref:System.Windows.Controls.ItemsControl>.</span></span>  <span data-ttu-id="fed02-180">Gdy <xref:System.Windows.Controls.ItemsControl> dane powiązane z kolekcją, kontener elementu jest generowany dla każdego elementu.</span><span class="sxs-lookup"><span data-stu-id="fed02-180">When an <xref:System.Windows.Controls.ItemsControl> is data bound to a collection, an item container is generated for each item.</span></span> <span data-ttu-id="fed02-181">W niektórych przypadkach kontenery elementu są usuwane z drzewa wizualnego.</span><span class="sxs-lookup"><span data-stu-id="fed02-181">In some cases, item containers are removed from the visual tree.</span></span> <span data-ttu-id="fed02-182">Są typowe przypadków, gdy kontener element zostanie usunięty po usunięciu elementu z kolekcji źródłowej i gdy jest włączona wirtualizacja na <xref:System.Windows.Controls.ItemsControl>.</span><span class="sxs-lookup"><span data-stu-id="fed02-182">Two typical cases where an item container is removed are when an item is removed from the underlying collection and when virtualization is enabled on the <xref:System.Windows.Controls.ItemsControl>.</span></span> <span data-ttu-id="fed02-183">W takich przypadkach <xref:System.Windows.FrameworkElement.DataContext%2A> obiektu kontenera elementu zostanie ustawiona do obiektu wskaźnikowych, który jest zwracany przez <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> właściwości statycznej.</span><span class="sxs-lookup"><span data-stu-id="fed02-183">In these cases, the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the item container will be set to the sentinel object that is returned by the <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A?displayProperty=nameWithType> static property.</span></span>  <span data-ttu-id="fed02-184">Należy sprawdzić, czy <xref:System.Windows.FrameworkElement.DataContext%2A> jest równa <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> obiektu przed uzyskaniem dostępu do <xref:System.Windows.FrameworkElement.DataContext%2A> kontenera elementu.</span><span class="sxs-lookup"><span data-stu-id="fed02-184">You should check whether the <xref:System.Windows.FrameworkElement.DataContext%2A> is equal to the <xref:System.Windows.Data.BindingOperations.DisconnectedSource%2A> object before accessing the <xref:System.Windows.FrameworkElement.DataContext%2A> of an item container.</span></span>  
  
<a name="live_shaping"></a>   
## <a name="repositioning-data-as-the-datas-values-change-live-shaping"></a><span data-ttu-id="fed02-185">Zmienianie położenia danych po zmianie wartości danych (kształtowania na żywo)</span><span class="sxs-lookup"><span data-stu-id="fed02-185">Repositioning data as the data's values change (Live shaping)</span></span>  
 <span data-ttu-id="fed02-186">Zbierania danych można grupowane, sortowane lub filtrowane.</span><span class="sxs-lookup"><span data-stu-id="fed02-186">A collection of data can be grouped, sorted, or filtered.</span></span> <span data-ttu-id="fed02-187">WPF 4.5 umożliwia danych można przestawiać modyfikacji danych.</span><span class="sxs-lookup"><span data-stu-id="fed02-187">WPF 4.5 enables the data to be rearranged when the data is modified.</span></span> <span data-ttu-id="fed02-188">Na przykład załóżmy, że aplikacja używa <xref:System.Windows.Controls.DataGrid> do listy zasobów w rynku zapasów i zasobów są sortowane według wartości zapasów.</span><span class="sxs-lookup"><span data-stu-id="fed02-188">For example, suppose that an application uses a <xref:System.Windows.Controls.DataGrid> to list stocks in a stock market and the stocks are sorted by stock value.</span></span> <span data-ttu-id="fed02-189">Jeśli sortowanie na żywo jest włączona na temat zasobów <xref:System.Windows.Data.CollectionView>, stock pozycja w <xref:System.Windows.Controls.DataGrid> przenosi, gdy wartość zasobów staje się większa lub mniejsza niż innym magazynie wartości.</span><span class="sxs-lookup"><span data-stu-id="fed02-189">If live sorting is enabled on the stocks' <xref:System.Windows.Data.CollectionView>, a stock's position in the <xref:System.Windows.Controls.DataGrid> moves when the value of the stock becomes greater or less than another stock's value.</span></span>   <span data-ttu-id="fed02-190">Aby uzyskać więcej informacji, zobacz <xref:System.ComponentModel.ICollectionViewLiveShaping> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="fed02-190">For more information, see the <xref:System.ComponentModel.ICollectionViewLiveShaping> interface.</span></span>  
  
<a name="weak_event_pattern"></a>   
## <a name="improved-support-for-establishing-a-weak-reference-to-an-event"></a><span data-ttu-id="fed02-191">Ulepszona obsługa ustanawianie słabe odwołanie do zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fed02-191">Improved Support for Establishing a Weak Reference to an Event</span></span>  
 <span data-ttu-id="fed02-192">Implementacja wzorca słabe zdarzeń jest teraz łatwiejsze, ponieważ subskrybentów zdarzeń mogą uczestniczyć w nim bez stosowania dodatkowy interfejs.</span><span class="sxs-lookup"><span data-stu-id="fed02-192">Implementing the weak event pattern is now easier because subscribers to events can participate in it without implementing an extra interface.</span></span>  <span data-ttu-id="fed02-193">Ogólnego <xref:System.Windows.WeakEventManager> klasa umożliwia również subskrybentów udziału we wzorcu słabe zdarzeń, jeśli jest to dedykowana <xref:System.Windows.WeakEventManager> nie istnieje dla określone zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="fed02-193">The generic <xref:System.Windows.WeakEventManager> class also enables subscribers to participate in the weak event pattern if a dedicated <xref:System.Windows.WeakEventManager> does not exist for a certain event.</span></span>  <span data-ttu-id="fed02-194">Aby uzyskać więcej informacji, zobacz [słabe wzorce zdarzeń](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="fed02-194">For more information, see [Weak Event Patterns](../../../../docs/framework/wpf/advanced/weak-event-patterns.md).</span></span>  
  
<a name="async"></a>   
## <a name="new-methods-for-the-dispatcher-class"></a><span data-ttu-id="fed02-195">Nowe metody dla klasy dyspozytora</span><span class="sxs-lookup"><span data-stu-id="fed02-195">New methods for the Dispatcher class</span></span>  
 <span data-ttu-id="fed02-196">Klasa dyspozytora definiuje nowych metod operacje synchroniczne i asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="fed02-196">The Dispatcher class defines new methods for synchronous and asynchronous operations.</span></span>  <span data-ttu-id="fed02-197">Synchroniczne <xref:System.Windows.Threading.Dispatcher.Invoke%2A> metoda definiuje przeciążeń, które przyjmują <xref:System.Action> lub <xref:System.Func%601> parametru.</span><span class="sxs-lookup"><span data-stu-id="fed02-197">The synchronous <xref:System.Windows.Threading.Dispatcher.Invoke%2A> method defines overloads that take an <xref:System.Action> or <xref:System.Func%601> parameter.</span></span> <span data-ttu-id="fed02-198">Nowych metod asynchronicznych <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, ma także <xref:System.Action> lub <xref:System.Func%601> jako parametru wywołania zwrotnego i zwraca <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>.</span><span class="sxs-lookup"><span data-stu-id="fed02-198">The new asynchronous method, <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, also takes an <xref:System.Action> or <xref:System.Func%601> as the callback parameter and returns a <xref:System.Windows.Threading.DispatcherOperation> or <xref:System.Windows.Threading.DispatcherOperation%601>.</span></span>   <span data-ttu-id="fed02-199"><xref:System.Windows.Threading.DispatcherOperation> i <xref:System.Windows.Threading.DispatcherOperation%601> klasy definiują <xref:System.Threading.Tasks.Task> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fed02-199">The <xref:System.Windows.Threading.DispatcherOperation> and <xref:System.Windows.Threading.DispatcherOperation%601> classes define a <xref:System.Threading.Tasks.Task> property.</span></span>  <span data-ttu-id="fed02-200">Podczas wywoływania <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, można użyć `await` — słowo kluczowe przy użyciu jednej <xref:System.Windows.Threading.DispatcherOperation> lub skojarzony <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="fed02-200">When you call <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>, you can use the `await` keyword with either the <xref:System.Windows.Threading.DispatcherOperation> or the associated <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="fed02-201">Jeśli musisz poczekać synchronicznie <xref:System.Threading.Tasks.Task> zwróconego przez <xref:System.Windows.Threading.DispatcherOperation> lub <xref:System.Windows.Threading.DispatcherOperation%601>, wywołaj <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> — metoda rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="fed02-201">If you need to wait synchronously for the <xref:System.Threading.Tasks.Task> that is returned by a <xref:System.Windows.Threading.DispatcherOperation> or <xref:System.Windows.Threading.DispatcherOperation%601>, call the <xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> extension method.</span></span> <span data-ttu-id="fed02-202">Wywoływanie <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> spowoduje zakleszczenie, jeśli operacja jest w kolejce w wątku wywołującym.</span><span class="sxs-lookup"><span data-stu-id="fed02-202">Calling <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> will result in a deadlock if the operation is queued on a calling thread.</span></span> <span data-ttu-id="fed02-203">Aby uzyskać więcej informacji o korzystaniu z <xref:System.Threading.Tasks.Task> do wykonywania asynchronicznych operacji, zobacz [równoległość zadań (Biblioteka zadań równoległych)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span><span class="sxs-lookup"><span data-stu-id="fed02-203">For more information about using a <xref:System.Threading.Tasks.Task> to perform asynchronous operations, see [Task Parallelism (Task Parallel Library)](../../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md).</span></span>  
  
<a name="events_markup_extenions"></a>   
## <a name="markup-extensions-for-events"></a><span data-ttu-id="fed02-204">Rozszerzenia znaczników dla zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fed02-204">Markup Extensions for Events</span></span>  
 <span data-ttu-id="fed02-205">WPF 4.5 obsługuje rozszerzenia znaczników dla zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="fed02-205">WPF 4.5 supports markup extensions for events.</span></span>  <span data-ttu-id="fed02-206">WPF nie definiuje rozszerzenie znacznika do użycia dla zdarzeń, można utworzyć rozszerzenia znaczników, który może służyć do zdarzeń są stron trzecich.</span><span class="sxs-lookup"><span data-stu-id="fed02-206">While WPF does not define a markup extension to be used for events, third parties are able to create a markup extension that can be used with events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fed02-207">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fed02-207">See Also</span></span>  
 [<span data-ttu-id="fed02-208">Co nowego w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fed02-208">What's New in the .NET Framework</span></span>](../../../../docs/framework/whats-new/index.md)
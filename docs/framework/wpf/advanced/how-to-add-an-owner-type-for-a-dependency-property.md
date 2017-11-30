---
title: "Jak dodać typ właściciela dla właściwości zależności"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 079f08e1c330b710748ea6bb1aab8ccfb7ae7016
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a><span data-ttu-id="77b32-102">Jak dodać typ właściciela dla właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="77b32-102">How to: Add an Owner Type for a Dependency Property</span></span>
<span data-ttu-id="77b32-103">W tym przykładzie przedstawiono sposób dodawania klasy jako właściciela właściwości zależności zarejestrowany dla innego typu.</span><span class="sxs-lookup"><span data-stu-id="77b32-103">This example shows how to add a class as an owner of a dependency property registered for a different type.</span></span> <span data-ttu-id="77b32-104">Dzięki temu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika właściwości systemu są i rozpoznawany jako właściciela dodatkowe właściwości klasy.</span><span class="sxs-lookup"><span data-stu-id="77b32-104">By doing this, the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] reader and property system are both able to recognize the class as an additional owner of the property.</span></span> <span data-ttu-id="77b32-105">Dodawanie jako właściciela opcjonalnie umożliwia dodawanie klasy do udostępnienia metadanych określonego typu.</span><span class="sxs-lookup"><span data-stu-id="77b32-105">Adding as owner optionally allows the adding class to provide type-specific metadata.</span></span>  
  
 <span data-ttu-id="77b32-106">W poniższym przykładzie `StateProperty` właściwość zarejestrowane przez `MyStateControl` klasy.</span><span class="sxs-lookup"><span data-stu-id="77b32-106">In the following example, `StateProperty` is a property registered by the `MyStateControl` class.</span></span> <span data-ttu-id="77b32-107">Klasa `UnrelatedStateControl` dodaje się jako właściciel `StateProperty` przy użyciu <xref:System.Windows.DependencyProperty.AddOwner%2A> metody, w szczególności za pomocą podpisu, który zezwala na nowe metadane dla właściwości zależności, ponieważ znajduje się na dodawanie typu.</span><span class="sxs-lookup"><span data-stu-id="77b32-107">The class `UnrelatedStateControl` adds itself as an owner of the `StateProperty` using the <xref:System.Windows.DependencyProperty.AddOwner%2A> method, specifically using the signature that allows for new metadata for the dependency property as it exists on the adding type.</span></span> <span data-ttu-id="77b32-108">Należy zauważyć, że należy zapewnić [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] metod dostępu właściwości, podobnie jak w przykładzie przedstawionym w [implementuje właściwości zależności](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) przykład, jak również ponownie udostępnić identyfikatora właściwości zależności klasy dodawane jako właściciel.</span><span class="sxs-lookup"><span data-stu-id="77b32-108">Notice that you should provide [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] accessors for the property similar to the example shown in the [Implement a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) example, as well as re-expose the dependency property identifier on the class being added as owner.</span></span>  
  
 <span data-ttu-id="77b32-109">Bez otoki, właściwości zależności będą nadal działać z punktu widzenia programowy dostęp przy użyciu <xref:System.Windows.DependencyObject.GetValue%2A> lub <xref:System.Windows.DependencyObject.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="77b32-109">Without wrappers, the dependency property would still work from the perspective of programmatic access using <xref:System.Windows.DependencyObject.GetValue%2A> or <xref:System.Windows.DependencyObject.SetValue%2A>.</span></span> <span data-ttu-id="77b32-110">Ale zwykle można równoległe to zachowanie właściwości systemu z [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] otoki właściwości.</span><span class="sxs-lookup"><span data-stu-id="77b32-110">But you typically want to parallel this property-system behavior with the [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] property wrappers.</span></span> <span data-ttu-id="77b32-111">Otoki ułatwić można ustawić właściwości zależności programowo i pozwala ustawić właściwości jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutów.</span><span class="sxs-lookup"><span data-stu-id="77b32-111">The wrappers make it easier to set the dependency property programmatically, and make it possible to set the properties as [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attributes.</span></span>  
  
 <span data-ttu-id="77b32-112">Aby dowiedzieć się, jak zastąpić domyślny metadanych, zobacz [zastąpienia metadane dla właściwości zależności](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span><span class="sxs-lookup"><span data-stu-id="77b32-112">To find out how to override default metadata, see [Override Metadata for a Dependency Property](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="77b32-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="77b32-113">Example</span></span>  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a><span data-ttu-id="77b32-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="77b32-114">See Also</span></span>  
 [<span data-ttu-id="77b32-115">Właściwości niestandardowe zależności</span><span class="sxs-lookup"><span data-stu-id="77b32-115">Custom Dependency Properties</span></span>](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [<span data-ttu-id="77b32-116">Przegląd właściwości zależności</span><span class="sxs-lookup"><span data-stu-id="77b32-116">Dependency Properties Overview</span></span>](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
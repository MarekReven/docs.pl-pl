---
title: "Porady: Ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9549fa11b3f019dce3cc77d5f6d1d08a8485f0cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="95fbc-102">Porady: Ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="95fbc-102">How to: Hide ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="95fbc-103">Ukrywanie elementów menu jest możliwość sterowania interfejsem użytkownika (UI), aplikacji i ograniczyć poleceń użytkownika.</span><span class="sxs-lookup"><span data-stu-id="95fbc-103">Hiding menu items is a way to control the user interface (UI) of your application and restrict user commands.</span></span> <span data-ttu-id="95fbc-104">Często chcesz ukryć całe menu, gdy wszystkich elementów menu na nim są niedostępne.</span><span class="sxs-lookup"><span data-stu-id="95fbc-104">Often, you will want to hide an entire menu when all of the menu items on it are unavailable.</span></span> <span data-ttu-id="95fbc-105">Przedstawia informacje o tym przeszkadzał dla użytkownika.</span><span class="sxs-lookup"><span data-stu-id="95fbc-105">This presents fewer distractions for the user.</span></span> <span data-ttu-id="95fbc-106">Ponadto możesz chcieć zarówno Ukryj i Wyłącz menu lub elementu menu, jak ukrywanie wyłącznie nie uniemożliwia użytkownikowi uzyskiwanie dostępu do polecenia menu za pomocą klawisza skrótu.</span><span class="sxs-lookup"><span data-stu-id="95fbc-106">Furthermore, you might want to both hide and disable the menu or menu item, as hiding alone does not prevent the user from accessing a menu command by using a shortcut key.</span></span> <span data-ttu-id="95fbc-107">Aby uzyskać więcej informacji dotyczących wyłączanie elementów menu, zobacz [porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="95fbc-107">For more information on disabling menu items, see [How to: Disable ToolStripMenuItems Using the Designer](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95fbc-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="95fbc-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="95fbc-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="95fbc-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="95fbc-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="95fbc-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a><span data-ttu-id="95fbc-111">Aby ukryć menu najwyższego poziomu i jego podmenu</span><span class="sxs-lookup"><span data-stu-id="95fbc-111">To hide a top-level menu and its submenu items</span></span>  
  
1.  <span data-ttu-id="95fbc-112">Wybierz element menu najwyższego poziomu i ustaw jej <xref:System.Windows.Forms.ToolStripItem.Visible%2A> lub <xref:System.Windows.Forms.ToolStripItem.Available%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="95fbc-112">Select the top-level menu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> or <xref:System.Windows.Forms.ToolStripItem.Available%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="95fbc-113">Ukrycie element menu najwyższego poziomu, również są ukryte wszystkich elementów menu w ramach danego menu.</span><span class="sxs-lookup"><span data-stu-id="95fbc-113">When you hide the top-level menu item, all menu items within that menu are also hidden.</span></span> <span data-ttu-id="95fbc-114">Jeśli klikniesz w innym miejscu niż na <xref:System.Windows.Forms.MenuStrip> po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Visible%2A> do `false`, element menu najwyższego poziomu całego i jego podmenu elementy są usuwane z formularza, w związku z tym przedstawiający efekt czasu wykonywania akcji.</span><span class="sxs-lookup"><span data-stu-id="95fbc-114">If you click somewhere other than on the <xref:System.Windows.Forms.MenuStrip> after setting <xref:System.Windows.Forms.ToolStripItem.Visible%2A> to `false`, the entire top-level menu item and its submenu items disappear from your form, thus showing you the run-time effect of your action.</span></span> <span data-ttu-id="95fbc-115">Aby wyświetlić element menu najwyższego poziomu ukryte w czasie projektowania, kliknij <xref:System.Windows.Forms.MenuStrip> w **zasobnik składnika**w **konspekt dokumentu**, lub w górnej części siatki właściwości.</span><span class="sxs-lookup"><span data-stu-id="95fbc-115">To display the hidden top-level menu item at design time, click on the <xref:System.Windows.Forms.MenuStrip> in the **Component Tray**, in **Document Outline**, or at the top of the property grid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95fbc-116">Rzadko spowoduje ukrycie całe menu z wyjątkiem wielu menu podrzędne interfejsu (MDI) dokumentu w scenariuszu scalania.</span><span class="sxs-lookup"><span data-stu-id="95fbc-116">You will rarely hide an entire menu except for multiple document interface (MDI) child menus in a merging scenario.</span></span>  
  
### <a name="to-hide-a-submenu-item"></a><span data-ttu-id="95fbc-117">Aby ukryć element podmenu</span><span class="sxs-lookup"><span data-stu-id="95fbc-117">To hide a submenu item</span></span>  
  
1.  <span data-ttu-id="95fbc-118">Wybierz element podmenu i ustaw jej <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="95fbc-118">Select the submenu item and set its <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property to `false`.</span></span>  
  
     <span data-ttu-id="95fbc-119">Ukrycie elementu podmenu pozostaje widoczne w formularzu w czasie projektowania, aby można go łatwo wybrać dalszej pracy.</span><span class="sxs-lookup"><span data-stu-id="95fbc-119">When you hide a submenu item, it remains visible on your form at design time so that you can easily select it for further work.</span></span> <span data-ttu-id="95fbc-120">Będzie ona faktycznie ukryta w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="95fbc-120">It will actually be hidden at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95fbc-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95fbc-121">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [<span data-ttu-id="95fbc-122">Informacje o formancie MenuStrip</span><span class="sxs-lookup"><span data-stu-id="95fbc-122">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="95fbc-123">Porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="95fbc-123">How to: Disable ToolStripMenuItems Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
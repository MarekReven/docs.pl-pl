---
title: "Porady: tworzenie programów do obsługi zdarzeń w czasie wykonywania dla formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handlers [Windows Forms], creating
- run time [Windows Forms], creating event handlers at
- examples [Windows Forms], event handling
- Button control [Windows Forms], event handlers
ms.assetid: 2e7c9e1a-61fe-444d-8113-3c5bacf1c8cb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 53664bcf8c776338399297687a16ec430bca128b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-event-handlers-at-run-time-for-windows-forms"></a><span data-ttu-id="68dd6-102">Porady: tworzenie programów do obsługi zdarzeń w czasie wykonywania dla formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68dd6-102">How to: Create Event Handlers at Run Time for Windows Forms</span></span>
<span data-ttu-id="68dd6-103">Oprócz tworzenia zdarzeń przy użyciu narzędzia Projektant formularzy systemu Windows, można również utworzyć program obsługi zdarzeń w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="68dd6-103">In addition to creating events using the Windows Forms Designer, you can also create an event handler at run time.</span></span> <span data-ttu-id="68dd6-104">Ta akcja umożliwia łączenie z na podstawie warunków w kodzie w czasie wykonywania, a nie przejdą oni połączone po początkowym uruchomieniu programu obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="68dd6-104">This action allows you to connect event handlers based on conditions in code at run time as opposed to having them connected when the program initially starts.</span></span>  
  
### <a name="to-create-an-event-handler-at-run-time"></a><span data-ttu-id="68dd6-105">Aby utworzyć program obsługi zdarzeń w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="68dd6-105">To create an event handler at run time</span></span>  
  
1.  <span data-ttu-id="68dd6-106">Otwórz go w edytorze kodu, który chcesz dodać do obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="68dd6-106">Open the form in the Code Editor that you want to add an event handler to.</span></span>  
  
2.  <span data-ttu-id="68dd6-107">Dodawanie metody do formularza z podpis metody dla zdarzenia, które mają być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="68dd6-107">Add a method to your form with the method signature for the event that you want to handle.</span></span>  
  
     <span data-ttu-id="68dd6-108">Na przykład, jeśli zostały obsługi <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> formantu, należy utworzyć metody, takie jak następujące:</span><span class="sxs-lookup"><span data-stu-id="68dd6-108">For example, if you were handling the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control, you would create a method such as the following:</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As EventArgs)  
       ' Add event handler code here.  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)   
    {  
    // Add event handler code here.  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,   
          System::EventArgs ^ e)  
       {  
          // Add event handler code here.  
       }  
    ```  
  
3.  <span data-ttu-id="68dd6-109">Dodaj kod, aby program obsługi zdarzeń, zależnie od potrzeb aplikacji.</span><span class="sxs-lookup"><span data-stu-id="68dd6-109">Add code to the event handler as appropriate to your application.</span></span>  
  
4.  <span data-ttu-id="68dd6-110">Określ, które formularza lub kontrolki, w którym chcesz utworzyć program obsługi zdarzeń dla.</span><span class="sxs-lookup"><span data-stu-id="68dd6-110">Determine which form or control you want to create an event handler for.</span></span>  
  
5.  <span data-ttu-id="68dd6-111">W przypadku metody w klasie formularza Dodaj kod, który określa program obsługi zdarzeń do obsługi zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="68dd6-111">In a method within your form's class, add code that specifies the event handler to handle the event.</span></span> <span data-ttu-id="68dd6-112">Na przykład następujący kod określa program obsługi zdarzeń `button1_Click` dojść <xref:System.Windows.Forms.Control.Click> zdarzenie <xref:System.Windows.Forms.Button> sterowania:</span><span class="sxs-lookup"><span data-stu-id="68dd6-112">For example, the following code specifies the event handler `button1_Click` handles the <xref:System.Windows.Forms.Control.Click> event of a <xref:System.Windows.Forms.Button> control:</span></span>  
  
    ```vb  
    AddHandler Button1.Click, AddressOf Button1_Click  
    ```  
  
    ```csharp  
    button1.Click += new EventHandler(button1_Click);  
    ```  
  
    ```cpp  
    button1->Click += gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     <span data-ttu-id="68dd6-113"><xref:System.ComponentModel.EventHandlerList.AddHandler%2A> Metody zostało to pokazane w powyższym kodzie Visual Basic ustanawia obsługi zdarzenia kliknięcia dla przycisku.</span><span class="sxs-lookup"><span data-stu-id="68dd6-113">The <xref:System.ComponentModel.EventHandlerList.AddHandler%2A> method demonstrated in the Visual Basic code above establishes a click event handler for the button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68dd6-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68dd6-114">See Also</span></span>  
 [<span data-ttu-id="68dd6-115">Tworzenie programów obsługi zdarzeń w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="68dd6-115">Creating Event Handlers in Windows Forms</span></span>](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [<span data-ttu-id="68dd6-116">Przegląd obsługi zdarzeń</span><span class="sxs-lookup"><span data-stu-id="68dd6-116">Event Handlers Overview</span></span>](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)  
 [<span data-ttu-id="68dd6-117">Rozwiązywanie problemów z odziedziczonymi programami obsługi zdarzeń w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68dd6-117">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
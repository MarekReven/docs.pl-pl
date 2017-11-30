---
title: "Międzynarodowe czcionki w formularzach i kontrolkach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts [Windows Forms], international
- international applications [Windows Forms], character display
- fonts [Windows Forms], globalization considerations
- localization [Windows Forms], fonts
- Windows Forms controls, labels
- font fallback in Windows Forms
- globalization [Windows Forms], character sets
ms.assetid: 2c3066df-9bac-479a-82b2-79e484b346a3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5901113021deffd601b5325ff9a1b8912e74329d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="international-fonts-in-windows-forms-and-controls"></a><span data-ttu-id="076d5-102">Międzynarodowe czcionki w formularzach i kontrolkach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="076d5-102">International Fonts in Windows Forms and Controls</span></span>
<span data-ttu-id="076d5-103">W aplikacjach międzynarodowych wybranie czcionki zalecaną metodą jest użycie rezerwa czcionek, tam gdzie to możliwe.</span><span class="sxs-lookup"><span data-stu-id="076d5-103">In International applications the recommended method of selecting fonts is to use font fallback wherever possible.</span></span> <span data-ttu-id="076d5-104">Czcionka rezerwowy oznacza, że system sprawdza, co skryptu znak należy do.</span><span class="sxs-lookup"><span data-stu-id="076d5-104">Font fallback means that the system determines what script the character belongs to.</span></span>  
  
## <a name="using-font-fallback"></a><span data-ttu-id="076d5-105">Przy użyciu rezerwa czcionek</span><span class="sxs-lookup"><span data-stu-id="076d5-105">Using Font Fallback</span></span>  
 <span data-ttu-id="076d5-106">Aby móc korzystać z tej funkcji, nie należy ustawiać <xref:System.Drawing.Font> właściwość formularza lub innego elementu.</span><span class="sxs-lookup"><span data-stu-id="076d5-106">To take advantage of this feature, do not set the <xref:System.Drawing.Font> property for your form or any other element.</span></span> <span data-ttu-id="076d5-107">Aplikacja będzie automatycznie używać domyślnej czcionki systemowej, która różni się od zlokalizowanego języka systemu operacyjnego do innego.</span><span class="sxs-lookup"><span data-stu-id="076d5-107">The application will automatically use the default system font, which differs from one localized language of the operating system to another.</span></span> <span data-ttu-id="076d5-108">Po uruchomieniu aplikacji, system automatycznie Podaj poprawną czcionkę dla kultury wybrane w systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="076d5-108">When the application runs, the system will automatically provide the correct font for the culture selected in the operating system.</span></span>  
  
 <span data-ttu-id="076d5-109">Brak wyjątek do reguły nie ustawienie czcionki, który jest zmiany stylu czcionki.</span><span class="sxs-lookup"><span data-stu-id="076d5-109">There is an exception to the rule of not setting the font, which is for changing the font style.</span></span> <span data-ttu-id="076d5-110">Może to być istotne dla aplikacji, w którym użytkownik kliknie przycisk, aby tekst w polu tekstowym wyświetlone pogrubioną czcionką.</span><span class="sxs-lookup"><span data-stu-id="076d5-110">This might be important for an application in which the user clicks a button to make text in a text box appear in boldface.</span></span> <span data-ttu-id="076d5-111">W tym celu piszesz funkcji, aby zmienić styl czcionki w polu tekstowym mają zostać pogrubione, oparte na czcionka niezależnie od formularza jest.</span><span class="sxs-lookup"><span data-stu-id="076d5-111">To do that, you would write a function to change the text box's font style to bold, based on whatever the form's font is.</span></span> <span data-ttu-id="076d5-112">Ważne jest, aby wywołanie tej funkcji w dwóch miejscach: w przycisku <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń i <xref:System.Windows.Forms.Control.FontChanged> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="076d5-112">It is important to call this function in two places: in the button's <xref:System.Windows.Forms.Control.Click> event handler and in the <xref:System.Windows.Forms.Control.FontChanged> event handler.</span></span> <span data-ttu-id="076d5-113">Jeśli funkcja jest wywoływana tylko w <xref:System.Windows.Forms.Control.Click> obsługi zdarzeń i inne części kodu zmienia rodziny czcionek całego formularza, pole tekstowe nie zmienia się w pozostałej części formularza.</span><span class="sxs-lookup"><span data-stu-id="076d5-113">If the function is called only in the <xref:System.Windows.Forms.Control.Click> event handler and some other piece of code changes the font family of the entire form, the text box will not change with the rest of the form.</span></span>  
  
```  
' Visual Basic  
Private Sub MakeBold()  
   ' Change the TextBox to a bold version of the form font  
   TextBox1.Font = New Font(Me.Font, FontStyle.Bold)  
End Sub  
  
Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
   ' Clicking this button makes the TextBox bold  
   MakeBold()  
End Sub  
  
Private Sub Form1_FontChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles MyBase.FontChanged  
   ' If the TextBox is already bold and the form's font changes,  
   ' change the TextBox to a bold version of the new form font  
   If (TextBox1.Font.Style = FontStyle.Bold) Then  
      MakeBold()  
   End If  
End Sub  
  
// C#  
private void button1_Click(object sender, System.EventArgs e)  
{  
   // Clicking this button makes the TextBox bold  
   MakeBold();  
}  
  
private void MakeBold()   
{  
   // Change the TextBox to a bold version of the form's font  
   textBox1.Font = new Font(this.Font, FontStyle.Bold);  
}  
  
private void Form1_FontChanged(object sender, System.EventArgs e)  
{  
   // If the TextBox is already bold and the form's font changes,  
   // change the TextBox to a bold version of the new form font  
   if (textBox1.Font.Style == FontStyle.Bold)   
   {  
      MakeBold();  
   }  
}  
```  
  
 <span data-ttu-id="076d5-114">Jednak gdy lokalizowanie aplikacji, pogrubioną czcionką mogą być wyświetlane nieprawidłowo określonych języków.</span><span class="sxs-lookup"><span data-stu-id="076d5-114">However, when you localize your application, the bold font may display poorly for certain languages.</span></span> <span data-ttu-id="076d5-115">W przypadku wątpliwości dotyczących ma wiadomość dla lokalizatorów dostępna będzie opcja przełączania czcionki czcionką na zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="076d5-115">If this is a concern, you want the localizers to have the option of switching the font from bold to regular text.</span></span> <span data-ttu-id="076d5-116">Ponieważ wiadomość dla lokalizatorów nie są zwykle deweloperzy i nie mają dostępu do kodu źródłowego, tylko do plików zasobów, ta opcja musi być ustawiona w plikach zasobów.</span><span class="sxs-lookup"><span data-stu-id="076d5-116">Since localizers are typically not developers and do not have access to source code, only to resource files, this option needs to be set in the resource files.</span></span> <span data-ttu-id="076d5-117">Aby to zrobić, należy ustawić <xref:System.Drawing.Font.Bold%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="076d5-117">To do this, you would set the <xref:System.Drawing.Font.Bold%2A> property to `true`.</span></span> <span data-ttu-id="076d5-118">Powoduje to ustawienie czcionki zapisaniem plików zasobów, gdy wiadomość dla lokalizatorów można go edytować.</span><span class="sxs-lookup"><span data-stu-id="076d5-118">This results in the font setting being written out to the resource files, where localizers can edit it.</span></span> <span data-ttu-id="076d5-119">Następnie napiszesz kod po `InitializeComponent` metoda czcionki oparte na jest bez względu na rodzaj czcionki, ale przy użyciu stylów czcionek określone w pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="076d5-119">You then write code after the `InitializeComponent` method to reset the font based on whatever the form's font is, but using the font style specified in the resource file.</span></span>  
  
```  
' Visual Basic  
TextBox1.Font = New System.Drawing.Font(Me.Font, TextBox1.Font.Style)  
  
// C#  
textBox1.Font = new System.Drawing.Font(this.Font, textBox1.Font.Style);  
```  
  
## <a name="see-also"></a><span data-ttu-id="076d5-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="076d5-120">See Also</span></span>  
 [<span data-ttu-id="076d5-121">Globalizacja formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="076d5-121">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)  
 [<span data-ttu-id="076d5-122">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="076d5-122">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
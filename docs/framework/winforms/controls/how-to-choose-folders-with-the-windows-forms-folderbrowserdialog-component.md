---
title: "Porady: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy systemu Windows"
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
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: de41d5664c2481032dffe213a52779834338ca2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>Porady: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy systemu Windows
Często w aplikacji systemu Windows, które możesz utworzyć, konieczne będzie monitować użytkowników, aby wybrać folder, większość często, aby zapisać zestawu plików. Formularze systemu Windows <xref:System.Windows.Forms.FolderBrowserDialog> składnik umożliwia łatwe wykonać to zadanie.  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>Aby wybrać folderów za pomocą składnika FolderBrowserDialog  
  
1.  W procedurze, sprawdź <xref:System.Windows.Forms.FolderBrowserDialog> składnika <xref:System.Windows.Forms.Form.DialogResult%2A> właściwości, aby zobaczyć, jak zostało zamknięte okno dialogowe i uzyskać wartość <xref:System.Windows.Forms.FolderBrowserDialog> składnika <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwości.  
  
2.  Do zestawu umieszczony najwyżej folderu, który pojawi się w widoku drzewa okna dialogowego należy ustawić <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> właściwość, która przyjmuje członkiem <xref:System.Environment.SpecialFolder> wyliczenia.  
  
3.  Ponadto można ustawić <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> właściwość, która określa ciąg znaków, który pojawi się w górnej części widoku drzewa folderu przeglądarki.  
  
     W poniższym przykładzie <xref:System.Windows.Forms.FolderBrowserDialog> składnika służy do wybierz folder, podobnie jak podczas tworzenia projektu w programie Visual Studio i wyświetlony monit o wybranie folder do zapisania go w. W tym przykładzie nazwa folderu jest następnie wyświetlane w <xref:System.Windows.Forms.TextBox> formantu w formularzu. Należy dobrze jest umieścić lokalizację w obszarze można edytować, takich jak <xref:System.Windows.Forms.TextBox> kontrolować, dzięki czemu użytkownicy mogą edytować ich wyboru, w przypadku błędu lub inne problemy. W tym przykładzie założono formularza z <xref:System.Windows.Forms.FolderBrowserDialog> składnika i <xref:System.Windows.Forms.TextBox> formantu.  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  Aby korzystać z tej klasy, z zestawu wymaga poziom uprawnień przyznanych przez <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> właściwość, która jest częścią programu <xref:System.Security.Permissions.FileIOPermissionAccess> wyliczenia. Jeśli używasz w kontekście częściowego zaufania, proces może zgłosić wyjątek, ze względu na niewystarczające uprawnienia. Aby uzyskać więcej informacji, zobacz [podstawy zabezpieczeń dostępu kodu](../../../../docs/framework/misc/code-access-security-basics.md).  
  
 Aby uzyskać informacje na temat zapisywania plików, zobacz [porady: zapisywanie plików za pomocą składnika SaveFileDialog](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [FolderBrowserDialog, składnik — omówienie (Windows Forms)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [FolderBrowserDialog, składnik](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)

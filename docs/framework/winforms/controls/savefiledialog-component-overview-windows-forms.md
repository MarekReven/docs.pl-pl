---
title: "SaveFileDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1505e2bc31afb4f44f0d635b06624528cb16ba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog — Informacje o składniku (Formularze systemu Windows)
Formularze systemu Windows <xref:System.Windows.Forms.SaveFileDialog> składnik jest okno dialogowe wstępnie skonfigurowane. Jest to standardowy **Zapisz plik** okno dialogowe używane przez system Windows. Dziedziczy on z <xref:System.Windows.Forms.CommonDialog> klasy.  
  
## <a name="working-with-the-savefiledialog-component"></a>Praca ze składnikiem SaveFileDialog  
 Używać go jako proste rozwiązanie umożliwiający użytkownikom zapisywanie plików zamiast konfigurować własne okno dialogowe. Polegając na standardowe okno dialogowe systemu Windows, podstawowe funkcje tworzenia aplikacji jest znane użytkowników. Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.SaveFileDialog> składnika, należy napisać logiki zapisywania plików.  
  
 Można użyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania. Plik można otworzyć w trybie odczytu/zapisu z użyciem <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.  
  
 Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.SaveFileDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog, składnik](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)

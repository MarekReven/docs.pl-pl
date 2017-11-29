---
title: "Porady: wstrzymywanie usług systemu Windows (Visual Basic)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: vb
f1_keywords: ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: d44358d3f76f50a06ede5e7d720f4f48d80893de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a>Porady: wstrzymywanie usług systemu Windows (Visual Basic)
W tym przykładzie użyto <xref:System.ServiceProcess.ServiceController> składnika można wstrzymać usługi administratora usług IIS na komputerze lokalnym.  
  
## <a name="example"></a>Przykład  
 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense. Selektor wstawek kodu, znajduje się się w **systemu operacyjnego Windows > usług systemu Windows**. Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołanie projektu do System.serviceprocess.dll.  
  
-   Dostęp do elementów członkowskich <xref:System.ServiceProcess> przestrzeni nazw. Dodaj `Imports` instrukcję, jeśli użytkownik jest całkowicie niekwalifikujących nazwy elementów członkowskich w kodzie. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
## <a name="robust-programming"></a>Niezawodne programowanie  
 <xref:System.ServiceProcess.ServiceController.MachineName%2A> Właściwość <xref:System.ServiceProcess.ServiceController> klasy jest komputerem lokalnym domyślnie. Aby odwołać usług systemu Windows na innym komputerze, należy zmienić <xref:System.ServiceProcess.ServiceController.MachineName%2A> właściwości nazwę tego komputera.  
  
 Następujące warunki mogą spowodować wyjątek:  
  
-   Nie można wstrzymać usługi. (<xref:System.InvalidOperationException>)  
  
-   Wystąpił błąd podczas uzyskiwania dostępu do interfejsu API systemu. (<xref:System.ComponentModel.Win32Exception>)  
  
## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework  
 Może być ograniczana kontroli usług na komputerze przy użyciu <xref:System.ServiceProcess.ServiceControllerPermissionAccess> można ustawić uprawnień <xref:System.ServiceProcess.ServiceControllerPermission>.  
  
 Dostęp do informacji o usłudze może być ograniczana przy użyciu <xref:System.Security.Permissions.PermissionState> można ustawić uprawnień <xref:System.Security.Permissions.SecurityPermission>.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceProcess.ServiceController>  
 <xref:System.ServiceProcess.ServiceControllerStatus>  
 <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>  
 [Porady: kontynuowanie usług systemu Windows (Visual Basic)](../../../docs/framework/windows-services/how-to-continue-a-windows-service-visual-basic.md)
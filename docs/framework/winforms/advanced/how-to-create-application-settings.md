---
title: "Porady: tworzenie ustawień aplikacji"
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
helpviewer_keywords:
- application settings [Windows Forms], Windows Forms
- application settings [Windows Forms], creating
ms.assetid: 1e7aa347-af75-41e5-89ca-f53cab704f72
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 481239b472ced5ef6251b665dad16e83a170607d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-application-settings"></a><span data-ttu-id="d2c59-102">Porady: tworzenie ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="d2c59-102">How to: Create Application Settings</span></span>
<span data-ttu-id="d2c59-103">Za pomocą kodu zarządzanego, można tworzyć nowe ustawienia aplikacji i powiązać je z właściwości formularza lub kontrolki formularza, aby te ustawienia są ładowane i automatycznie zapisywane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d2c59-103">Using managed code, you can create new application settings and bind them to properties on your form or your form's controls, so that these settings are loaded and saved automatically at run time.</span></span>  
  
 <span data-ttu-id="d2c59-104">W poniższej procedurze ręcznie utworzyć klasy otoki, która jest pochodną <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="d2c59-104">In the following procedure, you manually create a wrapper class that derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span> <span data-ttu-id="d2c59-105">Do tej klasy można dodać dostępny publicznie element właściwości dla każdego ustawienia aplikacji, które chcesz udostępnić.</span><span class="sxs-lookup"><span data-stu-id="d2c59-105">To this class you add a publicly accessible property for each application setting that you want to expose.</span></span>  
  
 <span data-ttu-id="d2c59-106">Można również wykonać tę procedurę przy użyciu minimalnego kodu w projektancie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d2c59-106">You can also perform this procedure using minimal code in the Visual Studio designer.</span></span>  <span data-ttu-id="d2c59-107">Zobacz też [porady: tworzenie aplikacji ustawienia przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d2c59-107">Also see [How to: Create Application Settings Using the Designer](http://msdn.microsoft.com/library/wabtadw6\(v=vs.110\)).</span></span>  
  
### <a name="to-create-new-application-settings-programmatically"></a><span data-ttu-id="d2c59-108">Aby utworzyć nowe ustawienia aplikacji programowo</span><span class="sxs-lookup"><span data-stu-id="d2c59-108">To create new Application Settings programmatically</span></span>  
  
1.  <span data-ttu-id="d2c59-109">Dodaj nową klasę do projektu i zmień jego nazwę.</span><span class="sxs-lookup"><span data-stu-id="d2c59-109">Add a new class to your project, and rename it.</span></span> <span data-ttu-id="d2c59-110">Do wykonania tej procedury, firma Microsoft będzie wywoływać tej klasy `MyUserSettings`.</span><span class="sxs-lookup"><span data-stu-id="d2c59-110">For this procedure, we will call this class `MyUserSettings`.</span></span> <span data-ttu-id="d2c59-111">Zmień definicję klasy, tak aby pochodną klasy <xref:System.Configuration.ApplicationSettingsBase>.</span><span class="sxs-lookup"><span data-stu-id="d2c59-111">Change the class definition so that the class derives from <xref:System.Configuration.ApplicationSettingsBase>.</span></span>  
  
2.  <span data-ttu-id="d2c59-112">Definiuje właściwości od tej klasy otoki dla każdego ustawienia aplikacji, potrzebujesz i zastosować tej właściwości przy użyciu jednej <xref:System.Configuration.ApplicationScopedSettingAttribute> lub <xref:System.Configuration.UserScopedSettingAttribute>, w zależności od zakresu ustawienia.</span><span class="sxs-lookup"><span data-stu-id="d2c59-112">Define a property on this wrapper class for each application setting you require, and apply that property with either the <xref:System.Configuration.ApplicationScopedSettingAttribute> or <xref:System.Configuration.UserScopedSettingAttribute>, depending on the scope of the setting.</span></span> <span data-ttu-id="d2c59-113">Aby uzyskać więcej informacji na temat zakres ustawień, zobacz [Przegląd ustawień aplikacji](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span><span class="sxs-lookup"><span data-stu-id="d2c59-113">For more information about settings scope, see [Application Settings Overview](../../../../docs/framework/winforms/advanced/application-settings-overview.md).</span></span> <span data-ttu-id="d2c59-114">W razie kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d2c59-114">By now, your code should look like this:</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
     [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
3.  <span data-ttu-id="d2c59-115">Utwórz wystąpienie tej klasy otoki w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2c59-115">Create an instance of this wrapper class in your application.</span></span> <span data-ttu-id="d2c59-116">Zwykle będzie prywatnego elementu członkowskiego formularza głównego.</span><span class="sxs-lookup"><span data-stu-id="d2c59-116">It will commonly be a private member of the main form.</span></span> <span data-ttu-id="d2c59-117">Teraz, gdy zdefiniowano klasy, należy powiązać go z właściwością; w takim przypadku <xref:System.Windows.Forms.Form.BackColor%2A> właściwości formularza.</span><span class="sxs-lookup"><span data-stu-id="d2c59-117">Now that you have defined your class, you need to bind it to a property; in this case, the <xref:System.Windows.Forms.Form.BackColor%2A> property of your form.</span></span> <span data-ttu-id="d2c59-118">Można to zrobić w formularza `Load` obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d2c59-118">You can accomplish this in your form's `Load` event handler.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#2)]
     [!code-vb[ApplicationSettings.Create#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="d2c59-119">Jeśli podasz sposób, aby zmienić ustawienia w czasie wykonywania, należy zapisać bieżące ustawienia użytkownika na dysku po zamknięciu formularza, w przeciwnym razie te zmiany zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="d2c59-119">If you provide a way to change settings at run time, you will need to save the user's current settings to disk when your form closes, or else these changes will be lost.</span></span>  
  
     [!code-csharp[ApplicationSettings.Create#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/Form1.cs#3)]
     [!code-vb[ApplicationSettings.Create#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/Form1.vb#3)]  
  
     <span data-ttu-id="d2c59-120">Teraz pomyślnie utworzono nowe ustawienie aplikacji i powiązany określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2c59-120">You have now successfully created a new application setting and bound it to the specified property.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d2c59-121">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="d2c59-121">.NET Framework Security</span></span>  
 <span data-ttu-id="d2c59-122">Domyślny dostawca ustawień <xref:System.Configuration.LocalFileSettingsProvider>, będzie nadal występował, informacje w plikach konfiguracji jako zwykły tekst.</span><span class="sxs-lookup"><span data-stu-id="d2c59-122">The default settings provider, <xref:System.Configuration.LocalFileSettingsProvider>, persists information to configuration files as plain text.</span></span> <span data-ttu-id="d2c59-123">To ogranicza zabezpieczeń w celu zabezpieczenia dostępu do plików obsługiwanych przez system operacyjny dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d2c59-123">This limits security to the file access security provided by the operating system for the current user.</span></span> <span data-ttu-id="d2c59-124">W związku z tym należy uważać z informacjami przechowywanymi w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d2c59-124">Because of this, care must be taken with the information stored in configuration files.</span></span> <span data-ttu-id="d2c59-125">Na przykład jednym z typowych zastosowań ustawienia aplikacji jest przechowywanie parametrów połączenia, wskazujące magazynu danych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2c59-125">For example, one common use for application settings is to store connection strings that point to the application's data store.</span></span> <span data-ttu-id="d2c59-126">Jednak ze względu na problemy z zabezpieczeniami, takich ciągów nie może zawierać hasła.</span><span class="sxs-lookup"><span data-stu-id="d2c59-126">However, because of security concerns, such strings should not include passwords.</span></span> <span data-ttu-id="d2c59-127">Aby uzyskać więcej informacji dotyczących parametrów połączenia, zobacz <xref:System.Configuration.SpecialSetting>.</span><span class="sxs-lookup"><span data-stu-id="d2c59-127">For more information about connection strings, see <xref:System.Configuration.SpecialSetting>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c59-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2c59-128">See Also</span></span>  
 <xref:System.Configuration.SpecialSettingAttribute>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [<span data-ttu-id="d2c59-129">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="d2c59-129">Application Settings Overview</span></span>](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [<span data-ttu-id="d2c59-130">Porady: Sprawdzanie poprawności ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="d2c59-130">How to: Validate Application Settings</span></span>](../../../../docs/framework/winforms/advanced/how-to-validate-application-settings.md)
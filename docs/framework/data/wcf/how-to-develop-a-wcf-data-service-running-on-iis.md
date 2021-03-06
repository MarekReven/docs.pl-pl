---
title: "Porady: Tworzenie usługi danych WCF działającą na serwerze IIS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93b6e8b6e687f2e39fd5792aba08eaa47fa29fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>Porady: Tworzenie usługi danych WCF działającą na serwerze IIS
W tym temacie przedstawiono sposób użycia [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Aby utworzyć usługę danych, która jest oparta na bazie danych Northwind hostowanej przez aplikacji sieci Web ASP.NET, która działa na Internet Information Services (IIS). Na przykład sposobu tworzenia tej samej usługi danych Northwind jako aplikacji sieci Web ASP.NET, która działa w ASP.NET Development Server zobacz [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
> [!NOTE]
>  Aby utworzyć usługę danych Northwind, musi zainstalowano przykładowej bazy danych Northwind na komputerze lokalnym. Aby pobrać tej przykładowej bazy danych, zobacz stronę pobierania [przykładowe bazy danych programu SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).  
  
 W tym temacie przedstawiono sposób tworzenia usługi danych przy użyciu dostawcy programu Entity Framework. Innych dostawców usług danych są dostępne. Aby uzyskać więcej informacji, zobacz [dostawców usług danych](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).  
  
 Po utworzeniu usługi musi jawnie zapewniają dostęp do zasobów usługi danych. Aby uzyskać więcej informacji, zobacz [porady: Włączanie dostępu do usługi Data](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a>Aby utworzyć aplikację sieci Web programu ASP.NET, która działa na serwerze IIS  
  
1.  W programie Visual Studio na **pliku** menu, wybierz opcję **nowy**, a następnie wybierz **projektu**.  
  
2.  W **nowy projekt** oknie dialogowym wybierz jako język programowania Visual Basic lub Visual C#.  
  
3.  W **szablony** okienku wybierz **aplikacji sieci Web ASP.NET**. Uwaga: Jeśli używasz programu Visual Studio Web Developer, należy utworzyć nową witrynę sieci Web zamiast nowej aplikacji sieci Web.  
  
4.  Typ `NorthwindService` jako nazwę projektu.  
  
5.  Kliknij przycisk **OK**.  
  
6.  Na **projektu** menu, wybierz opcję **NorthwindService właściwości**.  
  
7.  Wybierz **Web** , a następnie wybierz **użycia lokalnego serwera sieci Web usług IIS**.  
  
8.  Kliknij przycisk **utworzyć katalog wirtualny** , a następnie kliknij przycisk **OK**.  
  
9. W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):  
  
    -   systemy 32-bitowe:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   systemy 64-bitowe:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     Dzięki temu czy Windows Communication Foundation (WCF) jest zarejestrowana na komputerze.  
  
10. W wierszu polecenia z uprawnieniami administratora wykonaj jedną z następujących poleceń (w zależności od systemu operacyjnego):  
  
    -   systemy 32-bitowe:  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   systemy 64-bitowe:  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     Dzięki temu czy programu IIS działa poprawnie po zainstalowaniu na komputerze usługi WCF. Może być również ponowne uruchomienie usług IIS.  
  
11. Po uruchomieniu aplikacji ASP.NET w usługach IIS7, należy wykonać następujące czynności:  
  
    1.  Otwórz Menedżera usług IIS i przejdź do aplikacji PhotoService **domyślna witryna sieci Web**.  
  
    2.  W **widoku funkcji**, kliknij dwukrotnie **uwierzytelniania**.  
  
    3.  Na **uwierzytelniania** wybierz pozycję **uwierzytelnianie anonimowe**.  
  
    4.  W **akcje** okienku, kliknij przycisk **Edytuj** można ustawić zabezpieczeń, podmiotu zabezpieczeń, w których użytkownicy anonimowi będą połączyć się z witryną.  
  
    5.  W **edytowanie poświadczeń uwierzytelniania anonimowego** okno dialogowe, wybierz opcję **tożsamość puli aplikacji**.  
  
    > [!IMPORTANT]
    >  Gdy używasz konta Usługa sieciowa, udzielasz anonimowym wszystkich dostępu do sieci wewnętrznej powiązanej z tym kontem.  
  
12. Za pomocą programu SQL Server Management Studio, narzędzia sqlcmd.exe lub edytor języka Transact-SQL w programie Visual Studio, uruchom następujące polecenie języka Transact-SQL dla wystąpienia programu SQL Server, która ma dołączyć bazy danych Northwind:  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     Spowoduje to utworzenie nazwy logowania w wystąpieniu programu SQL Server dla konta systemu Windows używane do uruchamiania usług IIS. Dzięki temu usług IIS nawiązać połączenie z wystąpieniem serwera SQL.  
  
13. Z bazy danych Northwind dołączonej wykonaj następujące polecenia języka Transact-SQL:  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     Spowoduje to przydzielenie uprawnień do nowego identyfikatora użytkownika, który umożliwia usługom IIS do odczytu i zapisu danych do bazy danych Northwind.  
  
### <a name="to-define-the-data-model"></a>Aby zdefiniować modelu danych  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij przycisk **Dodaj nowy element.**  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **modelu danych jednostki ADO.NET**.  
  
3.  Wpisz nazwę modelu danych, `Northwind.edmx`.  
  
4.  W kreatorze modelu danych jednostki, wybierz **generowania z bazy danych**, a następnie kliknij przycisk **dalej**.  
  
5.  Połączenia z bazą danych modelu danych, wykonując jedną z następujących czynności, a następnie kliknij przycisk **dalej**:  
  
    -   Jeśli nie masz już skonfigurowane połączenie z bazą danych, kliknij przycisk **nowe połączenie** i Utwórz nowe połączenie. Aby uzyskać więcej informacji, zobacz [porady: tworzenie połączeń bazy danych programu SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631). To [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] wystąpienie musi mieć bazie danych Northwind dołączony.  
  
         \-lub -  
  
    -   Jeśli masz już skonfigurowana do łączenia z bazą danych Northwind połączenia z bazą danych, wybierz połączenie z listy połączeń.  
  
6.  Na ostatniej stronie kreatora zaznacz pola wyboru dla wszystkich tabel w bazie danych, a następnie usuń zaznaczenie pól wyboru dla widoków i procedur składowanych.  
  
7.  Kliknij przycisk **Zakończ** aby zamknąć kreatora.  
  
    > [!NOTE]
    >  Ten model danych wygenerowanych przedstawia właściwości klucza obcego w typach jednostek. Modeli danych utworzone za pomocą programu Visual Studio 2008 nie zawierają tych właściwości klucza obcego. W związku z tym należy zaktualizować żadnych aplikacji klienckich, które zostały utworzone w celu uzyskania dostępu do usługi danych Northwind, który został utworzony przy użyciu programu Visual Studio 2008 przed podjęciem próby wykonania tej wersji usługi danych Northwind dostępu do klasy usługi danych klienta.  
  
### <a name="to-create-the-data-service"></a>Aby utworzyć usługę danych  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę projektu ASP.NET, a następnie kliknij przycisk **Dodaj nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **usług danych ADO.NET**.  
  
3.  Wpisz nazwę usługi, `Northwind`.  
  
     Program Visual Studio tworzy pliki znaczników i kodu XML dla nowej usługi. Domyślnie zostanie otwarte okno edytora kodu. W **Eksploratora rozwiązań**, usługa będzie mieć nazwę, Northwind, z rozszerzeniem. svc.cs lub. svc.vb.  
  
4.  W kodzie dla usługi data, Zastąp komentarz `/* TODO: put your data source class name here */` w definicji klasy, która definiuje usługę danych o typie kontenera jednostek w modelu danych, który w tym przypadku jest `NorthwindEntities`. Definicja klasy powinien wyglądać to następujące czynności:  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a>Zobacz też  
 [Udostępnianie danych jako usługi](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)

---
title: Резервное копирование, восстановление и перемещение каталога служб SSIS | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
ms.assetid: bf806aef-8556-48ab-aed5-e95de9a2204e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: c5c4226b9ee4f45d7e732044379962489ecacd0f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62837514"
---
# <a name="backup-restore-and-move-the-ssis-catalog"></a>Резервное копирование, восстановление и перемещение каталога служб SSIS
  [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] включена база данных SSISDB. Создайте запрос представления в базе данных SSISDB для просмотра объектов, настроек и рабочих данных, которые хранятся в каталоге **SSISDB** . Этот раздел содержит инструкции для выполнения резервного копирования и восстановления базы данных.  
  
 В каталоге **SSISDB** хранятся пакеты, которые развернуты на сервере [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Дополнительные сведения о каталоге см. в разделе [Каталог служб SSIS](catalog/ssis-catalog.md).  
  
##  <a name="backup"></a> Создание резервной копии базы данных служб SSIS  
  
1.  Откройте среду [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] и установите соединение с экземпляром [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
2.  Создайте резервную копию главного ключа для базы данных SSISDB с помощью инструкции BACKUP MASTER KEY Transact-SQL. Ключ хранится в указанном файле. Используйте пароль для шифрования главного ключа базы данных в файле.  
  
     Дополнительные сведения об инструкции см. в разделе [BACKUP MASTER KEY (Transact-SQL)](/sql/t-sql/statements/backup-master-key-transact-sql).  
  
     В следующем примере главный ключ экспортируется в файл `c:\temp directory\RCTestInstKey` . Пароль `LS2Setup!` используется для шифрования главного ключа.  
  
    ```  
    backup master key to file = 'c:\temp\RCTestInstKey'  
           encryption by password = 'LS2Setup!'  
  
    ```  
  
3.  Выполните резервное копирование базы данных SSISDB с помощью диалогового окна **Создание резервной копии базы данных** в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Как создать резервную копию базы данных (среда SQL Server Management Studio)](https://go.microsoft.com/fwlink/?LinkId=231812).  
  
4.  Создайте скрипт CREATE LOGIN для ## MS_SSISServerCleanupJobLogin ##, выполнив следующие действия. Дополнительные сведения см. в разделе [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql).  
  
    1.  В обозревателе объектов среды [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]разверните узел **Безопасность** , а затем узел **Имена входа** .  
  
    2.  Щелкните правой кнопкой мыши **##MS_SSISServerCleanupJobLogin##** и выберите **Внести в скрипт имена входа как** > **СОЗДАТЬ в** > **В новом окне редактора запросов**.  
  
5.  Если планируется восстановление базы данных SSISDB из копии на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], где каталог SSISDB еще не создан, создайте скрипт CREATE PROCEDURE для sp_ssis_startup следующим образом. Дополнительные сведения см. в статье [CREATE PROCEDURE (Transact-SQL)](/sql/t-sql/statements/create-procedure-transact-sql).  
  
    1.  В обозревателе объектов разверните узел **Базы данных**, а затем узел **master** > **Программирование** > **Хранимые процедуры**.  
  
    2.  Щелкните правой кнопкой мыши **dbo.sp_ssis_startup**и выберите **Внести в скрипт хранимые процедуры как** > **СОЗДАТЬ в** > **В новом окне редактора запросов**.  
  
6.  Убедитесь, что агент SQL Server запущен.  
  
7.  Если планируется восстановление базы данных SSISDB из копии на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где каталог SSISDB еще не создан, создайте скрипт для задания обслуживания сервера SSIS следующим образом. Скрипт создается в агенте [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] автоматически при создании каталога SSISDB. Задание помогает очистить журналы операции с вышедшим сроком сохранения и удалить старые версии проектов.  
  
    1.  В обозревателе объектов разверните узел **Агент SQL Server** , а затем узел **Задания** .  
  
    2.  Щелкните правой кнопкой мыши задание по обслуживанию служб SSIS и выберите **Внести в скрипт задание как** > **СОЗДАТЬ в** > **В новом окне редактора запросов**.  
  
### <a name="to-restore-the-ssis-database"></a>Восстановление базы данных служб SSIS  
  
1.  Если база данных SSISDB восстанавливается из копии в экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], где каталог SSISDB никогда не создавался, включите среду CLR с помощью хранимой процедуры sp_configure. Дополнительные сведения см. в разделах [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) и [Параметр clr enabled](https://go.microsoft.com/fwlink/?LinkId=231855).  
  
    ```  
    use master   
           sp_configure 'clr enabled', 1  
           reconfigure  
  
    ```  
  
2.  Если база данных SSISDB восстанавливается из копии на экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где каталог SSISDB никогда не создавался, создайте асимметричный ключ и имя входа из асимметричного ключа и предоставьте разрешение UNSAFE для имени входа.  
  
    ```  
    Create Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey  
           FROM Executable File = 'C:\Program Files\Microsoft SQL Server\110\DTS\Binn\Microsoft.SqlServer.IntegrationServices.Server.dll'  
  
    ```  
  
     [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] требуют предоставления разрешения UNSAFE для имени входа, поскольку имени входа необходим дополнительный доступ к ресурсам, на которые существуют ограничения, например API-интерфейс Microsoft Win32. Дополнительные сведения о коде разрешения UNSAFE см. в разделе [Creating an Assembly](../relational-databases/clr-integration/assemblies/creating-an-assembly.md).  
  
    ```  
    Create Login MS_SQLEnableSystemAssemblyLoadingUser  
           FROM Asymmetric key MS_SQLEnableSystemAssemblyLoadingKey   
  
           Grant unsafe Assembly to MS_SQLEnableSystemAssemblyLoadingUser  
  
    ```  
  
3.  Восстановите базу данных SSISDB из резервной копии с помощью диалогового окна **Восстановление базы данных** в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в следующих разделах:  
  
    -   [Восстановление базы данных (страница "Общие")](general-page-of-integration-services-designers-options.md)  
  
    -   [Восстановление базы данных (страница "Файлы")](../relational-databases/backup-restore/restore-database-files-page.md)  
  
    -   [Восстановление базы данных (страница "Параметры")](../relational-databases/backup-restore/restore-database-options-page.md)  
  
4.  Выполните скрипт, созданный в разделе [Создание резервной копии базы данных служб SSIS](#backup) для ##MS_SSISServerCleanupJobLogin##, sp_ssis_startup и заданий по обслуживанию служб SSIS. Убедитесь, что агент SQL Server запущен.  
  
5.  Выполните следующую инструкцию для установки автоматического выполнения процедуры sp_ssis_startup. Дополнительные сведения см. в разделе [sp_procoption (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-procoption-transact-sql).  
  
    ```  
    EXEC sp_procoption N'sp_ssis_startup','startup','on'  
    ```  
  
6.  Сопоставьте пользователя SSISDB ##MS_SSISServerCleanupJobUser## (база данных SSISDB) с ##MS_SSISServerCleanupJobLogin## с помощью диалогового окна **Свойства имени входа** в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].  
  
7.  Восстановите главный ключ с помощью одного из следующих методов. Дополнительные сведения о шифровании см. в разделе [Encryption Hierarchy](../relational-databases/security/encryption/encryption-hierarchy.md).  
  
    -   **Метод 1**  
  
         Используйте этот метод при наличии резервной копии главного ключа базы данных и пароля, используемого для шифрования этого ключа.  
  
        ```  
               Restore master key from file = 'c:\temp\RCTestInstKey'  
               Decryption by password = 'LS2Setup!' -- 'Password used to encrypt the master key during SSISDB backup'  
               Encryption by password = 'LS3Setup!' -- 'New Password'  
               Force  
  
        ```  
  
        > [!NOTE]  
        >  Убедитесь, что учетная запись службы [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] имеет разрешения на чтение файла резервной копии ключа.  
  
        > [!NOTE]  
        >  Если главный ключ базы данных еще не зашифрован главным ключом сервера, то в среде [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] отобразится следующее предупреждающее сообщение. Пропустите это предупреждающее сообщение.  
        >   
        >  **Не удается расшифровать текущий главный ключ. Ошибка пропущена, так как задан параметр FORCE.**  
        >   
        >  Аргумент FORCE указывает, что следует продолжить процесс восстановления, даже если текущий главный ключ базы данных закрыт. Для каталога SSISDB это сообщение будет отображаться, поскольку главный ключ базы данных не является открытым в экземпляре, где осуществляется восстановление базы данных.  
  
    -   **Метод 2.**  
  
         Этот метод следует использовать при наличии исходного пароля, который использовался для создания SSISDB.  
  
        ```  
        open master key decryption by password = 'LS1Setup!' --'Password used when creating SSISDB'  
               Alter Master Key Add encryption by Service Master Key  
        ```  
  
8.  Определите, совместимы ли схема каталога SSISDB и двоичные файлы [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (сборка ISServerExec и SQLCLR), запустив [catalog.check_schema_version](/sql/integration-services/system-stored-procedures/catalog-check-schema-version).  
  
9. Для подтверждения того, что база данных SSISDB успешно восстановлена, выполните такие операции с каталогом SSISDB, как запуск пакетов, развернутых на сервере [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Дополнительные сведения см. разделе [Выполнение пакета на сервере служб SSIS с использованием среды SQL Server Management Studio](run-a-package-on-the-ssis-server-using-sql-server-management-studio.md).  
  
### <a name="to-move-the-ssis-database"></a>Перемещение базы данных служб SSIS  
  
-   Следуйте инструкциям по перемещению пользовательских баз данных. Дополнительные сведения см. в статье [Move User Databases](../relational-databases/databases/move-user-databases.md).  
  
     Обязательно создайте резервную копию главного ключа базы данных SSISDB и защитите файл резервной копии. Дополнительные сведения см. в статье [Создание резервной копии каталога SSISDB](#backup).  
  
     Убедитесь, что соответствующие объекты служб Integration Services (SSIS) созданы в новом экземпляре [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] , где каталог SSISDB еще не был создан.  
  
  

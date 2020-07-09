---
title: Создание профиля компонента Database Mail | Документация Майкрософт
ms.custom: ''
ms.date: 08/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Database Mail [SQL Server], public profiles
- profiles [SQL Server], Database Mail
- public profiles [Database Mail]
ms.assetid: 58ae749d-6ada-4f9c-bf00-de7c7a992a2d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 466fa0d08af2fa91aefa4d206037080a5aa8f0b3
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85737610"
---
# <a name="create-a-database-mail-profile"></a>Создание профиля компонента Database Mail
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
  Открытые и закрытые профили компонента Database Mail можно создать с помощью **мастера настройки компонента Database Mail** или [!INCLUDE[tsql](../../includes/tsql-md.md)] . Дополнительные сведения о профилях электронной почты см. в разделе [Профиль компонента Database Mail](database-mail-configuration-objects.md).
  
-   **Перед началом работы:** [Обязательные условия](#Prerequisites), [Безопасность](#Security)  
  
-   **Создание закрытого профиля компонента Database Mail с использованием:**  [мастера настройки компонента Database Mail](#SSMSProcedure), [Transact-SQL](#PrivateProfile)  
  
-   **Создание открытого профиля компонента Database Mail с использованием:**  [мастера настройки компонента Database Mail](#SSMSProcedure), [Transact-SQL](#PublicProfile)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> Предварительные требования  
 Создайте одну или несколько учетных записей компонента Database Mail для профиля. Дополнительные сведения о создании компонента Database Mail см. в разделе [Создание учетной записи компонента Database Mail](../../relational-databases/database-mail/create-a-database-mail-account.md).  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
 Открытый профиль дает возможность всем пользователям получать доступ к базе данных **msdb** , отправив туда почтовое сообщение из этого профиля. Персональный профиль может использоваться как пользователем, так и ролью. Предоставление роли доступа к профилю создает более простую обслуживаемую архитектуру. Для отправки почты пользователь должен быть членом роли **DatabaseMailUserRole** в базе данных **msdb** , а также иметь доступ как минимум к одному профилю Database Mail.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Пользователь, создающий учетные записи профилей и выполняющий хранимые процедуры, должен быть членом предопределенной роли сервера sysadmin.  
  
##  <a name="using-database-mail-configuration-wizard"></a><a name="SSMSProcedure"></a> Использование мастера настройки компонента Database Mail  
 **Создание профиля компонента Database Mail**  
  
-   В обозревателе объектов подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , для которого необходимо настроить компонент Database Mail, и разверните дерево сервера.  
  
-   Разверните узел **Управление**  
  
-   Дважды щелкните компонент Database Mail, чтобы открыть мастер настройки компонента Database Mail.  
  
-   На странице **Выбор задачи настройки** выберите **Управление учетными записями и профилями компонента Database Mail** и нажмите кнопку **Далее**.  
  
-   На странице **Управление профилями и учетными записями** выберите команду **Создать новый профиль** и нажмите кнопку **Далее**.  
  
-   На странице **Создать профиль** задайте имя профиля и описание, а также добавьте учетные записи, которые будут включены в профиль, после чего нажмите кнопку **Далее**.  
  
-   На странице **Завершение работы мастера** просмотрите действия, которые будут выполнены, и нажмите кнопку **Готово** , чтобы завершить создание нового профиля.  
  
-   **Настройка закрытого профиля компонента Database Mail.**  
  
    -   Откройте мастер настройки компонента Database Mail.  
  
    -   На странице **Выбор задачи настройки** выберите **Управление учетными записями и профилями компонента Database Mail** и нажмите кнопку **Далее**.  
  
    -   На странице **Управление учетными записями и профилями** выберите **Управление безопасностью профилей** и нажмите кнопку **Далее**.  
  
    -   На вкладке **Закрытые профили** установите флажок для профиля, который необходимо настроить, и нажмите кнопку **Далее**.  
  
    -   На странице **Завершение работы мастера** просмотрите действия, которые необходимо выполнить, и нажмите кнопку **Готово** , чтобы завершить настройку профиля.  
  
-   **Настройка открытого профиля компонента Database Mail.**  
  
    -   Откройте мастер настройки компонента Database Mail.  
  
    -   На странице **Выбор задачи настройки** выберите **Управление учетными записями и профилями компонента Database Mail** и нажмите кнопку **Далее**.  
  
    -   На странице **Управление учетными записями и профилями** выберите **Управление безопасностью профилей** и нажмите кнопку **Далее**.  
  
    -   На вкладке **Открытые профили** установите флажок для профиля, который необходимо настроить, и нажмите кнопку **Далее**.  
  
    -   На странице **Завершение работы мастера** просмотрите действия, которые необходимо выполнить, и нажмите кнопку **Готово** , чтобы завершить настройку профиля.  
  
## <a name="using-transact-sql"></a>Использование Transact-SQL  
  
###  <a name="to-create-a-database-mail-private-profile"></a><a name="PrivateProfile"></a> Создание закрытого профиля компонента Database Mail  
  
-   Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Чтобы создать новый профиль, выполните системную хранимую процедуру [sysmail_add_profile_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md) следующим образом:  
  
     **EXECUTEmsdb.dbo.sysmail_add_profile_sp**  
  
     *\@profile_name* = '*Имя профиля*'  
  
     *\@description* = '*Описание*'  
  
     *\@profile_name* — имя профиля, а *\@description* — описание профиля. Это необязательный параметр.  
  
-   Для каждой учетной записи выполните хранимую процедуру [sysmail_add_profileaccount_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md), как показано ниже.  
  
     **EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**  
  
     *\@profile_name* = '*Имя профиля*'  
  
     *\@account_name* = '*Имя учетной записи*'  
  
     *\@sequence_number* = '*порядковый номер учетной записи в профиле.* '  
  
     *\@profile_name* — имя профиля, *\@account_name* — имя учетной записи, добавляемой к профилю, а *\@sequence_number* определяет порядок использования учетных записей в профиле.  
  
-   Всем ролям или пользователям баз данных, отправляющим письма с использованием этого профиля, следует предоставить доступ к профилю. Для этого выполните хранимую процедуру [sysmail_add_principalprofile_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql.md), как показано ниже.  
  
     **EXECUTEmsdb.sysmail_add_principalprofile_sp**  
  
     *\@profile_name* = '*Имя профиля*'  
  
     *\@principal_name* = '*Имя пользователя или роли базы данных*'  
  
     *\@is_default* = '*Состояние профиля по умолчанию* '  
  
     *\@profile_name* — имя профиля, *\@principal_name* — имя пользователя или роли базы данных, а *\@is_default* определяет, является ли этот профиль профилем по умолчанию для пользователя или роли базы данных.  
  
 В следующем примере создается учетная запись компонента Database Mail, создается закрытый профиль компонента Database Mail, затем учетная запись добавляется к профилю и предоставляется доступ к профилю для роли базы данных **DBMailUsers** в базе данных **msdb** .  
  
```  
-- Create a Database Mail account  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Administrator',  
    @description = 'Mail account for administrative e-mail.',  
    @email_address = 'dba@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @account_name = 'AdventureWorks Administrator',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to the DBMailUsers role  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Administrator Profile',  
    @principal_name = 'ApplicationUser',  
    @is_default = 1 ;  
```  
  
###  <a name="to-create-a-database-mail-public-profile"></a><a name="PublicProfile"></a> Создание открытого профиля компонента Database Mail  
  
-   Подключитесь к экземпляру [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Чтобы создать новый профиль, выполните системную хранимую процедуру [sysmail_add_profile_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-add-profile-sp-transact-sql.md) следующим образом:  
  
     **EXECUTEmsdb.dbo.sysmail_add_profile_sp**  
  
     *\@profile_name* = '*Имя профиля*'  
  
     *\@description* = '*Описание*'  
  
     *\@profile_name* — имя профиля, а *\@description* — описание профиля. Это необязательный параметр.  
  
-   Для каждой учетной записи выполните хранимую процедуру [sysmail_add_profileaccount_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-add-profileaccount-sp-transact-sql.md), как показано ниже.  
  
     **EXECUTEmsdb.dbo.sysmail_add_profileaccount_sp**  
  
     *\@profile_name* = '*Имя профиля*'  
  
     *\@account_name* = '*Имя учетной записи*'  
  
     *\@sequence_number* = '*порядковый номер учетной записи в профиле.* '  
  
     *\@profile_name* — имя профиля, *\@account_name* — имя учетной записи, добавляемой к профилю, а *\@sequence_number* определяет порядок использования учетных записей в профиле.  
  
-   Чтобы предоставить открытый доступ, выполните хранимую процедуру [sysmail_add_principalprofile_sp (Transact-SQL)](../../relational-databases/system-stored-procedures/sysmail-add-principalprofile-sp-transact-sql.md), как показано ниже.  
  
     **EXECUTEmsdb.sysmail_add_principalprofile_sp**  
  
     *\@profile_name* = '*Имя профиля*'  
  
     *\@ principal_name* = '**открытый** или **0**'  
  
     *\@is_default* = '*Состояние профиля по умолчанию* '  
  
     *\@profile_name* — имя профиля, *\@principal_name* указывает, что этот профиль является общим, а *\@is_default* определяет, является ли он профилем по умолчанию для пользователя или роли базы данных.  
  
 В следующем примере создается учетная запись компонента Database Mail, создается закрытый профиль компонента Database Mail, затем учетная запись добавляется к профилю и предоставляется общий доступ к профилю.  
  
```  
-- Create a Database Mail account  
  
EXECUTE msdb.dbo.sysmail_add_account_sp  
    @account_name = 'AdventureWorks Public Account',  
    @description = 'Mail account for use by all database users.',  
    @email_address = 'db_users@Adventure-Works.com',  
    @replyto_address = 'danw@Adventure-Works.com',  
    @display_name = 'AdventureWorks Automated Mailer',  
    @mailserver_name = 'smtp.Adventure-Works.com' ;  
  
-- Create a Database Mail profile  
  
EXECUTE msdb.dbo.sysmail_add_profile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @description = 'Profile used for administrative mail.' ;  
  
-- Add the account to the profile  
  
EXECUTE msdb.dbo.sysmail_add_profileaccount_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @account_name = 'AdventureWorks Public Account',  
    @sequence_number =1 ;  
  
-- Grant access to the profile to all users in the msdb database  
  
EXECUTE msdb.dbo.sysmail_add_principalprofile_sp  
    @profile_name = 'AdventureWorks Public Profile',  
    @principal_name = 'public',  
    @is_default = 1 ;  
```  
  
  

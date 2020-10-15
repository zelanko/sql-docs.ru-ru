---
description: Make a Master Server
title: Make a Master Server
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.msxwiz.operator.f1
- sql13.ag.msxwiz.login.f1
- sql13.ag.msxwiz.target.f1
- sql13.ag.msxwiz.complete.f1
- sql13.ag.msxwiz.cover.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: markingmyname
ms.author: maghan
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 4f7d4af9a2e2b35ebb2ac10a594141a4fa7ca9a5
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92034923"
---
# <a name="make-a-master-server"></a>Make a Master Server
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]

> [!IMPORTANT]  
> В [Управляемом экземпляре Azure SQL](/azure/sql-database/sql-database-managed-instance) в настоящее время поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия в T-SQL между Управляемым экземпляром SQL Azure и SQL Server](/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается, как создать главный сервер [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="security"></a><a name="Security"></a>безопасность  
Распределенные задания, имеющие связанные с учетной записью-посредником шаги, выполняются в контексте учетной записи-посредника на целевом сервере. Убедитесь в том, что выполняются нижеприведенные условия, либо в том, что шаги заданий, связанные с учетной записью-посредником, не будут загружаться с главного сервера на целевой:  
  
-   Подраздел реестра главного сервера **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<&#42;имя_экземпляра&#42;>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) имеет значение 1 (true). По умолчанию для него задается значение 0 (false).  
  
-   На целевом сервере есть учетная запись-посредник. Ее имя совпадает с именем учетной записи-посредника на главном сервере, под которой выполняется шаг задания.  
  
Если шаги задания, использующие учетную запись-посредник, завершаются с ошибками при скачивании с главного сервера на целевой, то в столбце **error_message** в таблице **sysdownloadlist** базы данных **msdb** появятся следующие сообщения об ошибках:  
  
-   «Для этого шага задания необходима учетная запись-посредник, однако проверка совпадения учетной записи-посредника на целевом сервере отключена.»  
  
    Чтобы устранить эту ошибку, задайте для раздела реестра **AllowDownloadedJobsToMatchProxyName** значение 1.  
  
-   «Учетная запись-посредник не найдена.»  
  
    Чтобы устранить эту ошибку, убедитесь, что на целевом сервере есть учетная запись-посредник, имя которой совпадает с именем посреднической учетной записи на главном сервере, под которой выполняется шаг задания.  
  
#### <a name="permissions"></a><a name="Permissions"></a>Permissions  
По умолчанию разрешения на выполнение этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-make-a-master-server"></a>Создание главного сервера  
  
1.  В **обозревателе объектов** подключитесь к экземпляру [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)] и разверните его.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите **Администрирование нескольких серверов**и выберите пункт **Сделать главным**. **Мастер настройки главного сервера** служит проводником по созданию главного сервера и добавлению целевых серверов.  
  
3.  На странице **Оператор главного сервера** настройте оператора для главного сервера. Чтобы отправлять уведомления операторам по электронной почте или на пейджеры, необходимо настроить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для отправки электронной почты. Для отправки уведомлений операторам с использованием команды **net send**на сервере, где установлен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , должна быть запущена служба сообщений.  
  
    **Адрес электронной почты**  
    Адрес электронной почты оператора.  
  
    **Адрес пейджера**  
    Адрес электронной почты пейджера оператора.  
  
    **Адрес для команды net send**  
    Задает адрес **net send** для оператора.  
  
4.  На странице **Целевой сервер** выберите целевые серверы для главного сервера.  
  
    **зарегистрированные серверы**  
    Выводит серверы, зарегистрированные в среде Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , которые еще не являются целевыми.  
  
    **Целевые серверы**  
    Выводит серверы, являющиеся целевыми серверами.  
  
    **>**  
    Перемещает выбранный сервер в список целевых серверов.  
  
    **>>**  
    Перемещает все серверы в список целевых серверов.  
  
    **<**  
    Удаляет выбранный сервер из списка целевых серверов.  
  
    **<<**  
    Удаляет все серверы из списка целевых серверов.  
  
    **Добавить соединение**  
    Добавляет сервер в список целевых серверов без регистрации.  
  
    **Соединение**  
    Измените свойства соединения выбранного сервера.  
  
5.  Страница **Учетные данные для входа на главный сервер** используется для создания в случае необходимости нового имени входа для целевого сервера и для назначения этому имени прав на главном сервере.  
  
    **Создать новое имя входа (если необходимо) и присвоить ему права на главный сервер**  
    Если указанное имя входа еще не существует, создайте на целевом сервере новое имя входа.  
  
## <a name="using-transact-sql"></a><a name="TsqlProcedure"></a>Использование Transact-SQL  
  
#### <a name="to-make-a-master-server"></a>Создание главного сервера  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере текущий сервер прикрепляется к главному серверу AdventureWorks1. Расположение текущего сервера: строение 21, комната 309, стойка 5.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
Дополнительные сведения см. в разделе [sp_msx_enlist (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql.md).  
  
## <a name="see-also"></a>См. также:  
[Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)  
[Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  

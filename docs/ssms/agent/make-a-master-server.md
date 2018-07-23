---
title: Создание главного сервера | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-agent
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
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
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 65b89207e6a532b7e9583da0c571857663a885d6
ms.sourcegitcommit: c7a98ef59b3bc46245b8c3f5643fad85a082debe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2018
ms.locfileid: "38985486"
---
# <a name="make-a-master-server"></a>Make a Master Server
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Сейчас в [управляемом экземпляре базы данных SQL Azure](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance) поддерживается большинство функций агента SQL Server (но не все). Подробные сведения см. в статье [Различия T-SQL между управляемым экземпляром базы данных SQL Azure и SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

В этом разделе описывается, как создать главный сервер [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] или [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**В этом разделе**  
  
-   **Перед началом работы**  
  
    [безопасность](#Security)  
  
-   **Для создания главного сервера используется:**  
  
    [Среда SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Перед началом  
  
### <a name="Security"></a>безопасность  
Распределенные задания, имеющие связанные с учетной записью-посредником шаги, выполняются в контексте учетной записи-посредника на целевом сервере. Убедитесь в том, что выполняются нижеприведенные условия, либо в том, что шаги заданий, связанные с учетной записью-посредником, не будут загружаться с главного сервера на целевой:  
  
-   Подраздел реестра главного сервера **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<&#42;имя_экземпляра&#42;>\SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) имеет значение 1 (true). По умолчанию для него задается значение 0 (false).  
  
-   На целевом сервере есть учетная запись-посредник. Ее имя совпадает с именем учетной записи-посредника на главном сервере, под которой выполняется шаг задания.  
  
Если шаги задания, использующие учетную запись-посредник, завершаются с ошибками при скачивании с главного сервера на целевой, то в столбце **error_message** в таблице **sysdownloadlist** базы данных **msdb** появятся следующие сообщения об ошибках:  
  
-   «Для этого шага задания необходима учетная запись-посредник, однако проверка совпадения учетной записи-посредника на целевом сервере отключена.»  
  
    Чтобы устранить эту ошибку, задайте для раздела реестра **AllowDownloadedJobsToMatchProxyName** значение 1.  
  
-   «Учетная запись-посредник не найдена.»  
  
    Чтобы устранить эту ошибку, убедитесь, что на целевом сервере есть учетная запись-посредник, имя которой совпадает с именем посреднической учетной записи на главном сервере, под которой выполняется шаг задания.  
  
#### <a name="Permissions"></a>Permissions  
По умолчанию разрешения на выполнение этой процедуры имеют члены предопределенной роли сервера **sysadmin** .  
  
## <a name="SSMSProcedure"></a>Использование среды SQL Server Management Studio  
  
#### <a name="to-make-a-master-server"></a>Создание главного сервера  
  
1.  В **обозревателе объектов** подключитесь к экземпляру компонента [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]и разверните узел этого экземпляра.  
  
2.  Щелкните правой кнопкой мыши элемент **Агент SQL Server**, укажите **Администрирование нескольких серверов**и выберите пункт **Сделать главным**. **Мастер настройки главного сервера** служит проводником по созданию главного сервера и добавлению целевых серверов.  
  
3.  На странице **Оператор главного сервера** настройте оператора для главного сервера. Чтобы отправлять уведомления операторам по электронной почте или на пейджеры, необходимо настроить агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] для отправки электронной почты. Для отправки уведомлений операторам с использованием команды **net send**на сервере, где установлен агент [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] , должна быть запущена служба сообщений.  
  
    **Адрес электронной почты**  
    Адрес электронной почты оператора.  
  
    **Адрес пейджера**  
    Адрес электронной почты пейджера оператора.  
  
    **Адрес для команды net send**  
    Задает адрес **net send** для оператора.  
  
4.  На странице **Целевой сервер** выберите целевые серверы для главного сервера.  
  
    **зарегистрированные серверы**  
    Выводит серверы, зарегистрированные в среде Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] , которые еще не являются целевыми.  
  
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
  
## <a name="TsqlProcedure"></a>Использование Transact-SQL  
  
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
  
Дополнительные сведения см. в разделе [sp_msx_enlist (Transact-SQL)](http://msdn.microsoft.com/ceb3b2bc-0cc4-48d8-9bdc-6a809556e35f).  
  
## <a name="see-also"></a>См. также:  
[Создание многосерверной среды](../../ssms/agent/create-a-multiserver-environment.md)  
[Автоматизация администрирования в масштабах предприятия](../../ssms/agent/automated-administration-across-an-enterprise.md)  
  

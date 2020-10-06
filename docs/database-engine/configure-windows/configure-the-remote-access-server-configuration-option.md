---
title: Настройка параметра конфигурации сервера "remote access" | Документы Майкрософт
description: Узнайте об альтернативах устаревшего параметра remote access. Просмотрите другие источники по устранению неполадок, связанных с подключениями к SQL Server.
ms.custom: ''
ms.date: 08/11/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], stored procedure execution
ms.assetid: f5de748d-1c55-4714-9661-38fe62e5095f
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 62ed4ee20e7a17b291b09f895f7a558b91584ee9
ms.sourcegitcommit: 2f868a77903c1f1c4cecf4ea1c181deee12d5b15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2020
ms.locfileid: "91670297"
---
# <a name="configure-the-remote-access-server-configuration-option"></a>Настройка параметра конфигурации сервера remote access
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Эта статья посвящена компоненту "Удаленный доступ". Этот параметр конфигурации является довольно запутанной и устаревшей возможностью взаимодействия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с другим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и пользоваться ей совершенно незачем. Если вы попали на эту страницу, пытаясь устранить неполадки с подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], рекомендуем изучить какую-нибудь из следующих статей:  
  
-   [Руководство. Начало работы с ядром СУБД](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
  
-   [Вход в систему SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
-   [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
-   [Подключение к зарегистрированному серверу (среда SQL Server Management Studio)](../../ssms/register-servers/connect-to-a-registered-server-sql-server-management-studio.md)  
  
-   [Подключение к любому компоненту сервера SQL Server из среды SQL Server Management Studio](../../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
  
-   [Подключение к компоненту Database Engine при помощи программы sqlcmd](../../ssms/scripting/sqlcmd-connect-to-the-database-engine.md)  
  
-   [Поиск и устранение неполадок соединений с SQL Server Database Engine](https://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
 Программистам могут быть интересны следующие статьи.  
  
-   [Руководство. Подключение к SQL Server с помощью проверки подлинности SQL в ASP.NET 2.0](/previous-versions/msp-n-p/ff648340(v=pandp.10))  
  
-   [Соединение с экземпляром SQL Server](../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)  
  
-   [Руководство. Создание подключений к базам данных SQL Server](/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))  
  
 **Основная часть этой статьи начинается здесь.**  
  
 В этом разделе описываются способы настройки параметра конфигурации сервера **remote access** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **remote access** управляет выполнением хранимых процедур на локальных или удаленных серверах, на которых запущены экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение этого параметра по умолчанию равно 1. Это предоставляет разрешение на запуск локальных хранимых процедур с удаленных серверов или удаленных хранимых процедур с локального сервера. Значение параметра 0 предотвращает запуск локальных хранимых процедур с удаленных серверов или удаленных хранимых процедур на локальном сервере.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Вместо этого используйте хранимую процедуру [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md).
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра remote access с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра remote access](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Параметр **remote access** применим только к серверам, добавленным при помощи хранимой процедуры [sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), и включен только в целях обратной совместимости.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-access-option"></a>Настройка параметра remote access  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Выберите узел **Соединения** .  
  
3.  В диалоговом окне **Удаленные серверные соединения**установите или сбросьте флажок **Разрешить удаленные соединения с этим сервером** .  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-remote-access-option"></a>Настройка параметра remote access  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `remote access` равным `0`.  
  
```sql  
EXEC sp_configure 'remote access', 0 ;  
GO  
RECONFIGURE ;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-remote-access-option"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметра remote access  
 Этот параметр вступит в силу после перезапуска SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  

---
title: Настройка параметра конфигурации сервера "remote access" | Документы Майкрософт
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
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 52d6f73b585f3d0857186bef9c6c440e8655adc1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68012340"
---
# <a name="configure-the-remote-access-server-configuration-option"></a>Настройка параметра конфигурации сервера remote access
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  Эта статья посвящена компоненту "Удаленный доступ". Этот параметр конфигурации является довольно запутанной и устаревшей возможностью взаимодействия [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с другим [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и пользоваться ей совершенно незачем. Если вы попали на эту страницу, пытаясь устранить неполадки с подключением к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], рекомендуем изучить какую-нибудь из следующих статей:  
  
-   [Учебник. Начало работы с ядром СУБД](../../relational-databases/tutorial-getting-started-with-the-database-engine.md)  
  
-   [Вход в систему SQL Server](../../database-engine/configure-windows/logging-in-to-sql-server.md)  
  
-   [Подключение к SQL Server в случае, если доступ системных администраторов заблокирован](../../database-engine/configure-windows/connect-to-sql-server-when-system-administrators-are-locked-out.md)  
  
-   [Подключение к зарегистрированному серверу (среда SQL Server Management Studio)](../../tools/sql-server-management-studio/connect-to-a-registered-server-sql-server-management-studio.md)  
  
-   [Подключение к любому компоненту сервера SQL Server из среды SQL Server Management Studio](../../ssms/f1-help/connect-to-any-sql-server-component-from-sql-server-management-studio.md)  
  
-   [Подключение к компоненту Database Engine при помощи программы sqlcmd](../../relational-databases/scripting/sqlcmd-connect-to-the-database-engine.md)  
  
-   [Поиск и устранение неполадок соединений с SQL Server Database Engine](https://social.technet.microsoft.com/wiki/contents/articles/2102.how-to-troubleshoot-connecting-to-the-sql-server-database-engine.aspx)  
  
 Программистам могут быть интересны следующие статьи.  
  
-   [Руководство. Подключение к SQL Server с помощью проверки подлинности SQL в ASP.NET 2.0](https://msdn.microsoft.com/library/ff648340.aspx)  
  
-   [Соединение с экземпляром SQL Server](../../relational-databases/server-management-objects-smo/create-program/connecting-to-an-instance-of-sql-server.md)  
  
-   [Руководство. Создание подключений к базам данных SQL Server](https://msdn.microsoft.com/library/s4yys16a.aspx)  
  
 **Основная часть этой статьи начинается здесь.**  
  
 В этом разделе описываются способы настройки параметра конфигурации сервера **remote access** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **remote access** управляет выполнением хранимых процедур на локальных или удаленных серверах, на которых запущены экземпляры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Значение этого параметра по умолчанию равно 1. Это предоставляет разрешение на запуск локальных хранимых процедур с удаленных серверов или удаленных хранимых процедур с локального сервера. Значение параметра 0 предотвращает запуск локальных хранимых процедур с удаленных серверов или удаленных хранимых процедур на локальном сервере.  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepNextDontUse](../../includes/ssnotedepnextdontuse-md.md)] Вместо этого используйте хранимую процедуру [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md) .
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра remote access с помощью**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра remote access](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   Параметр **remote access** применим только к серверам, добавленным при помощи хранимой процедуры [sp_addserver](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md), и включен только в целях обратной совместимости.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-remote-access-option"></a>Настройка параметра remote access  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Выберите узел **Соединения** .  
  
3.  В диалоговом окне **Удаленные серверные соединения**установите или сбросьте флажок **Разрешить удаленные соединения с этим сервером** .  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
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
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра remote access  
 Этот параметр вступит в силу после перезапуска SQL Server.  
  
## <a name="see-also"></a>См. также:  
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)  
  
  

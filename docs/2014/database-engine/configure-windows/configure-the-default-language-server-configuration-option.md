---
title: Настройка параметра конфигурации сервера "default language" | Документы Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- default language option
ms.assetid: c08c26d8-5a62-487e-a4ee-4c529e4f9287
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 2ca958583cbdf6fec00d5d507051f10be503abf4
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48079744"
---
# <a name="configure-the-default-language-server-configuration-option"></a>Настройка параметра конфигурации сервера «язык по умолчанию»
  В этом разделе описываются способы настройки параметра конфигурации сервера **default language** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **default language** определяет язык по умолчанию для всех вновь создаваемых имен входа. Чтобы задать язык по умолчанию, укажите значение **langid** нужного языка. Значение параметра **langid** может быть получено путем выполнения запроса к представлению совместимости **sys.syslanguages** .  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра default language с помощью различных средств.**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия**  [После настройки параметра default language](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Язык по умолчанию для имени входа может быть переопределен при помощи инструкции CREATE LOGIN или ALTER LOGIN. Для сеанса языком по умолчанию является язык имени входа, используемого этим сеансом, если только он не был переопределен в сеансе при помощи интерфейса ODBC или OLE DB. Следует отметить, что параметру **default language** может быть присвоен только идентификатор языка, определенный в представлении совместимости [sys.syslanguages](/sql/relational-databases/system-compatibility-views/sys-syslanguages-transact-sql) (0–32). При использовании автономных баз данных для базы данных можно задать язык по умолчанию с помощью инструкции CREATE DATABASE или ALTER DATABASE, а для пользователей автономной базы данных можно использовать инструкцию CREATE USER или ALTER USER. При настройке языков по умолчанию в автономной базе данных принимается значение **langid** , имена или псевдонимы языков, приведенные в представлении совместимости **sys.syslanguages**.  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-default-language-option"></a>Настройка параметра default language  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Прочие параметры сервера** .  
  
3.  В поле **Язык пользователей по умолчанию** выберите язык, на котором [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] будет отображать системные сообщения.  
  
     По умолчанию используется английский язык.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-default-language-option"></a>Настройка параметра default language  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `default language` равным "Французский" (`2`).  
  
```tsql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'default language', 2 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра default language  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также  
 [CREATE LOGIN (Transact-SQL)](/sql/t-sql/statements/create-login-transact-sql)   
 [ALTER LOGIN (Transact-SQL)](/sql/t-sql/statements/alter-login-transact-sql)   
 [CREATE USER (Transact-SQL)](/sql/t-sql/statements/create-user-transact-sql)   
 [ALTER USER (Transact-SQL)](/sql/t-sql/statements/alter-user-transact-sql)   
 [CREATE DATABASE (SQL Server Transact-SQL)](/sql/t-sql/statements/create-database-sql-server-transact-sql)   
 [ALTER DATABASE (Transact-SQL)](/sql/t-sql/statements/alter-database-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

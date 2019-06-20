---
title: Настройка параметра конфигурации сервера "media retention" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- backup retention duration [SQL Server]
- backup sets [SQL Server], retention duration
- media retention option
ms.assetid: 12e9fe6a-20a5-4c6e-9cc9-d500c003b70a
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d9e936c25db4522a949fb97257e136ba6799697f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62811349"
---
# <a name="configure-the-media-retention-server-configuration-option"></a>Настройка параметра сервера media retention
  В этом разделе описывается настройка параметра конфигурации сервера **media retention** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **media retention** используется для указания времени хранения каждого резервного набора данных. Этот параметр обеспечивает защиту резервных копий от перезаписи до истечения установленного числа суток. После настройки параметра **media retention** не нужно определять длительность хранения резервных копий системы каждый раз, когда выполняется резервное копирование. Значение по умолчанию — 0 дней, максимальное — 365 дней.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Рекомендации](#Recommendations)  
  
     [безопасность](#Security)  
  
-   **Настройка параметра media retention с помощью следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра media retention](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="Restrictions"></a> Ограничения  
  
-   При использовании носителя данных резервных копий до истечения установленного количества суток служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выдает предупреждающее сообщение. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не выдает предупреждений, если настройки по умолчанию не были изменены.  
  
###  <a name="Recommendations"></a> Рекомендации  
  
-   Этот параметр является дополнительным и его следует изменять только опытным администраторам баз данных или сертифицированным техническим специалистам [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Параметр **media retention** можно переопределить с помощью предложения RETAINDAYS инструкции [BACKUP](/sql/t-sql/statements/backup-transact-sql) .  
  
###  <a name="Security"></a> безопасность  
  
####  <a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-media-retention-option"></a>Настройка параметра media retention  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Параметры базы данных** .  
  
3.  В области **Резервное копирование и восстановление**в поле **Срок хранения носителей резервных копий по умолчанию** введите или выберите значение от 0 до 365, чтобы установить время в сутках, в течение которого будут храниться носители данных резервных копий после создания резервной копии журнала транзакций или базы данных.  
  
##  <a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-media-retention-option"></a>Настройка параметра media retention  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование хранимой процедуры [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) для задания значения параметра `media retention` равным `60` дням.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'media retention', 60 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md).  
  
##  <a name="FollowUp"></a> Дальнейшие действия. После настройки параметра media retention  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также  
 [Резервное копирование и восстановление баз данных SQL Server](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)   
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [RECONFIGURE (Transact-SQL)](/sql/t-sql/language-elements/reconfigure-transact-sql)   
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  

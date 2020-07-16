---
title: Настройка параметра конфигурации сервера max text repl size | Документы Майкрософт
description: Сведения о том, как использовать параметр max text repl size для установки ограничений на размер определенных типов данных, которые SQL Server добавляет к реплицируемому или отслеживаемому столбцу.
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- max text repl size option
ms.assetid: 3056cf64-621d-4996-9162-3913f6bc6d5b
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 372bf3cfbe8aa3138bad7e03cc6c666c09ad68d5
ms.sourcegitcommit: 21c14308b1531e19b95c811ed11b37b9cf696d19
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2020
ms.locfileid: "86159712"
---
# <a name="configure-the-max-text-repl-size-server-configuration-option"></a>Настройка параметра конфигурации сервера max text repl size
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sql-asdbmi.md)]

  В этом разделе описываются способы настройки параметра конфигурации сервера **max text repl size** в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или [!INCLUDE[tsql](../../includes/tsql-md.md)]. Параметр **max text repl size** используется для указания максимального размера (в байтах) типов данных **text**, **ntext**, **varchar(max)** , **nvarchar(max)** , **varbinary(max)** , **xml**и **image** , которые могут добавляться к реплицируемому или отслеживаемому столбцу в инструкции INSERT, UPDATE, WRITETEXT или UPDATETEXT. Значение по умолчанию — 65 536 байт. Значение -1 означает отсутствие ограничений размера, кроме тех, которые налагаются типом данных.  
  
 **В этом разделе**  
  
-   **Перед началом работы**  
  
     [Ограничения](#Restrictions)  
  
     [Безопасность](#Security)  
  
-   **Настройка параметра max text repl size с использованием следующих средств:**  
  
     [Среда SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Дальнейшие действия.**  [После настройки параметра max text repl size](#FollowUp)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Ограничения  
  
-   Этот параметр применим только к репликации транзакций и системе отслеживания измененных данных. Если сервер настроен как для репликации транзакций, так и для системы отслеживания измененных данных, заданное значение применяется к обеим функциям. При репликации моментальных снимков и репликации слиянием этот параметр не учитывается.  
  
###  <a name="security"></a><a name="Security"></a> безопасность  
  
####  <a name="permissions"></a><a name="Permissions"></a> Permissions  
 Разрешения на выполнение хранимой процедуры **sp_configure** без параметров или только с первым параметром по умолчанию предоставляются всем пользователям. Для выполнения процедуры **sp_configure** с обоими параметрами для изменения параметра конфигурации или запуска инструкции RECONFIGURE необходимо иметь разрешение ALTER SETTINGS на уровне сервера. Разрешение ALTER SETTINGS неявным образом предоставлено предопределенным ролям сервера **sysadmin** и **serveradmin** .  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Использование среды SQL Server Management Studio  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a>Настройка параметра max text repl size  
  
1.  В обозревателе объектов щелкните правой кнопкой мыши сервер и выберите пункт **Свойства**.  
  
2.  Щелкните узел **Дополнительно** .  
  
3.  Во вкладке **Разное**задайте для параметра **max text repl size** нужное значение.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Использование Transact-SQL  
  
#### <a name="to-configure-the-max-text-repl-size-option"></a>Настройка параметра max text repl size  
  
1.  Установите соединение с компонентом [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  На панели «Стандартная» нажмите **Создать запрос**.  
  
3.  Скопируйте следующий пример в окно запроса и нажмите кнопку **Выполнить**. В этом примере описывается использование процедуры [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) для задания значения параметра `max text repl size` равным `-1`.  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1 ;   
RECONFIGURE ;   
GO  
EXEC sp_configure 'max text repl size', -1 ;   
GO  
RECONFIGURE;   
GO  
  
```  
  
 Дополнительные сведения см. в разделе [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md).  
  
##  <a name="follow-up-after-you-configure-the-max-text-repl-size-option"></a><a name="FollowUp"></a> Дальнейшие действия. После настройки параметра max text repl size  
 Параметр вступает в силу немедленно, без перезапуска сервера.  
  
## <a name="see-also"></a>См. также:  
 [Репликация SQL Server](../../relational-databases/replication/sql-server-replication.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [RECONFIGURE (Transact-SQL)](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)   
 [UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)   
 [WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)  
  
  

---
title: DBCC INPUTBUFFER (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 04/04/2018
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC INPUTBUFFER
- INPUTBUFFER
- DBCC_INPUTBUFFER_TSQL
- INPUTBUFFER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- input buffers [SQL Server]
- last statement from client
- displaying last statement sent
- statements [SQL Server], last statement
- DBCC INPUTBUFFER statement
ms.assetid: a44d702b-b3fb-4950-8c8f-1adcf3f514ba
author: pmasl
ms.author: umajay
manager: craigg
ms.openlocfilehash: 22891968234e0ad81e95e6aa78c76a2f8e5d4910
ms.sourcegitcommit: 0a7beb2f51e48889b4a85f7c896fb650b208eb36
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/09/2019
ms.locfileid: "57685381"
---
# <a name="dbcc-inputbuffer-transact-sql"></a>DBCC INPUTBUFFER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Отображает последнюю инструкцию, отправленную клиентом экземпляру [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC INPUTBUFFER ( session_id [ , request_id ])  
[WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
*session_id*  
Идентификатор сеанса, связанный с каждым активным первичным соединением.  
  
*request_id*  
Строгий (пакетный) запрос для поиска в текущем сеансе.  

Аргумент *request_id* возвращается с помощью следующего запроса:  
```sql
SELECT request_id   
FROM sys.dm_exec_requests   
WHERE session_id = @@spid;  
```  
на  
Позволяет задавать параметры.  
  
NO_INFOMSGS  
Подавляет все информационные сообщения со степенями серьезности от 0 до 10.  
  
## <a name="result-sets"></a>Результирующие наборы  
DBCC INPUTBUFFER возвращает набор строк со следующими столбцами.
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**EventType**|**nvarchar(30)**|Тип события. Может быть **RPC Event** или **Language Event**. Если последние события не обнаружены, на выходе будет **No Event**.|  
|**Параметры**|**smallint**|0 = Текст<br /><br /> 1- *n* = параметры|  
|**EventInfo**|**nvarchar(4000)**|Если столбец **EventType** имеет значение RPC, столбец **EventInfo** содержит лишь имя процедуры. Для значения Language столбца **EventType** выводятся только первые 4000 символов события.|  
  
Например, в случае, когда последним событием в буфере было DBCC INPUTBUFFER(11), инструкция DBCC INPUTBUFFER возвращает следующий результирующий набор.
  
```
EventType      Parameters EventInfo               
-------------- ---------- ---------------------   
Language Event 0          DBCC INPUTBUFFER (11)  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления  2 (SP2) используйте процедуру [sys.dm_exec_input_buffer](../../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md) для возврата сведений об инструкциях, переданных в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="permissions"></a>Разрешения  
В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется выполнение одного из следующих условий:
-   пользователь должен быть членом предопределенной роли сервера **sysadmin**;  
-   у пользователя должно быть разрешение VIEW SERVER STATE;  
-   идентификатор сеанса (*session_id*) должен быть равным идентификатору сеанса, с которым выполняется команда. Для определения идентификатора сеанса выполните следующий запрос:  
  
```sql
SELECT @@spid;  
```
  
В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] для уровней "Премиум" и "Критически важный для бизнеса" необходимо разрешение VIEW DATABASE STATE в базе данных. В [!INCLUDE[ssSDS](../../includes/sssds-md.md)] для уровней "Стандартный", "Базовый" и "Общего назначения" требуется учетная запись администратора [!INCLUDE[ssSDS](../../includes/sssds-md.md)].
  
## <a name="examples"></a>Примеры  
В следующем примере инструкция `DBCC INPUTBUFFER` выполняется по второму соединению, в то время как по ранее установленному соединению выполняется длинная транзакция.
  
```sql
CREATE TABLE dbo.T1 (Col1 int, Col2 char(3));  
GO  
DECLARE @i int = 0;  
BEGIN TRAN  
SET @i = 0;  
WHILE (@i < 100000)  
BEGIN  
INSERT INTO dbo.T1 VALUES (@i, CAST(@i AS char(3)));  
SET @i += 1;  
END;  
COMMIT TRAN;  
--Start new connection #2.  
DBCC INPUTBUFFER (52);  
```  

## <a name="see-also"></a>См. также:  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)  
[sys.dm_exec_input_buffer (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md)
  
  

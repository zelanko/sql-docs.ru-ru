---
title: "Инструкция DBCC INPUTBUFFER (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 10/13/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
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
caps.latest.revision: 51
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 54e4c8309c290255cb2885fab04bb394bc453046
ms.openlocfilehash: 3d9b6acfbfef3125d6ee715708492de1cae2b3a2
ms.contentlocale: ru-ru
ms.lasthandoff: 10/16/2017

---
# <a name="dbcc-inputbuffer-transact-sql"></a>DBCC INPUTBUFFER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

Отображает последнюю инструкцию, отправляемые с клиента на экземпляр [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```sql
DBCC INPUTBUFFER ( session_id [ , request_id ])  
[WITH NO_INFOMSGS ]  
```  
  
## <a name="arguments"></a>Аргументы  
*session_id*  
Идентификатор сеанса, связанный с каждым активным первичным соединением.  
  
*идентификатор_запроса*  
Строгий (пакетный) запрос для поиска в текущем сеансе.  

Следующий запрос возвращает *request_id*:  
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
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**Тип события**|**nvarchar(30)**|Тип события. Это может быть **RPC Event** или **события языка**. Выходные данные будут **No Event** при нет последние события не обнаружены.|  
|**Параметры**|**smallint**|0 = Текст<br /><br /> 1 -  *n*  = параметры|  
|**EventInfo**|**nvarchar(4000)**|Для **EventType** из RPC, **EventInfo** содержит только имя процедуры. Для **EventType** языка, отображаются только первые 4000 символов события.|  
  
Например, в случае, когда последним событием в буфере было DBCC INPUTBUFFER(11), инструкция DBCC INPUTBUFFER возвращает следующий результирующий набор.
  
```
EventType      Parameters EventInfo               
-------------- ---------- ---------------------   
Language Event 0          DBCC INPUTBUFFER (11)  
  
(1 row(s) affected)  
  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  

> [!NOTE]
> Начиная с [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SP2, используйте [sys.dm_exec_input_buffer](../../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md) для возвращения сведений об инструкциях, отправленных в экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="permissions"></a>Permissions  
На [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] требуется один из следующих:
-   Пользователь должен быть членом **sysadmin** предопределенной роли сервера.  
-   у пользователя должно быть разрешение VIEW SERVER STATE;  
-   *session_id* должен совпадать с Идентификатором сеанса, в которой выполняется команда. Для определения идентификатора сеанса выполните следующий запрос:  
  
```sql
SELECT @@spid;  
```
  
На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Premium необходимо разрешение VIEW DATABASE STATE в базе данных. На [!INCLUDE[ssSDS](../../includes/sssds-md.md)] уровней Standard и Basic требуется [!INCLUDE[ssSDS](../../includes/sssds-md.md)] учетная запись администратора.
  
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
[sys.dm_exec_input_buffer &#40; Transact-SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-input-buffer-transact-sql.md)
  
  


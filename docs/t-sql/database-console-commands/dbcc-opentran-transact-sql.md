---
title: DBCC OPENTRAN (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 11/14/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DBCC_OPENTRAN_TSQL
- DBCC OPENTRAN
- OPENTRAN_TSQL
- OPENTRAN
dev_langs:
- TSQL
helpviewer_keywords:
- status information [SQL Server], transactions
- transactions [SQL Server], status information
- DBCC OPENTRAN statement
- open transactions
- displaying transaction information
- checking open transactions
- oldest transactions [SQL Server]
ms.assetid: 63163843-226f-42d3-9e2c-b634fbf06943
author: pmasl
ms.author: umajay
ms.openlocfilehash: 02a90a155bcfcc2ad2294fb03c4e8b832701e36c
ms.sourcegitcommit: 8ffc23126609b1cbe2f6820f9a823c5850205372
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2020
ms.locfileid: "81632408"
---
# <a name="dbcc-opentran-transact-sql"></a>DBCC OPENTRAN (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

Инструкция DBCC OPENTRAN помогает определить активные транзакции, которые могут препятствовать усечению журнала. Инструкция DBCC OPENTRAN отображает сведения о самой старой активной транзакции и о самых старых реплицированных транзакциях, распределенных и нераспределенных, если таковые имеются в журнале транзакций указанной базы данных. Результаты отображаются только при наличии активной транзакции, которая приведена в журнале, или в случае, если в базе данных имеются сведения о репликации. Если в журнале нет активных транзакций, отображается информационное сообщение.
  
> [!NOTE]
>  DBCC OPENTRAN не поддерживается для издателей, отличных от издателей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
DBCC OPENTRAN   
[   
    ( [ database_name | database_id | 0 ] )   
    { [ WITH TABLERESULTS ]  
      [ , [ NO_INFOMSGS ] ]  
    }  
]   
```  
  
## <a name="arguments"></a>Аргументы  
 *database_name* | *database_id*| 0  
 Имя или идентификатор базы данных, для которой необходимо отобразить сведения о самой давней транзакции. Если значение не указано или указано значение 0, используется текущая база данных. Имена баз данных должны соответствовать правилам [идентификаторов](../../relational-databases/databases/database-identifiers.md).  
  
 TABLERESULTS  
 Указывает, что результаты должны выводиться в табличном формате, чтобы их можно было загрузить в таблицу. Используйте этот параметр для создания таблицы результатов, которые могут быть вставлены в таблицу для сравнений. Если этот аргумент не указан, результаты форматируются так, чтобы они были более удобочитаемыми.  
  
 NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks  
Используйте инструкцию DBCC OPENTRAN, чтобы определить, существует ли открытая транзакция в журнале транзакций. При выполнении инструкции BACKUP LOG только неактивная часть журнала может быть усечена; открытая транзакция может помешать полному усечению журнала транзакций. Для определения открытой транзакции получите идентификатор системного процесса, выполнив инструкцию sp_who.
  
## <a name="result-sets"></a>Результирующие наборы  
Инструкция DBCC OPENTRAN возвращает следующий результирующий набор, если нет открытых транзакций:
  
```sql
No active open transactions.  
DBCC execution completed. If DBCC printed error messages, contact your system administrator.  
```  
  
## <a name="permissions"></a>Разрешения  
Необходимо быть членом предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** .
  
## <a name="examples"></a>Примеры  
### <a name="a-returning-the-oldest-active-transaction"></a>A. Возвращение самой старой активной транзакции  
В следующем примере сведения о транзакциях извлекаются для текущей базы данных. Полученные результаты могут отличаться от приведенных ниже.
  
```sql  
CREATE TABLE T1(Col1 int, Col2 char(3));  
GO  
BEGIN TRAN  
INSERT INTO T1 VALUES (101, 'abc');  
GO  
DBCC OPENTRAN;  
ROLLBACK TRAN;  
GO  
DROP TABLE T1;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
Transaction information for database 'master'.
Oldest active transaction:
SPID (server process ID) : 52
UID (user ID) : -1
Name          : user_transaction
LSN           : (518:1576:1)
Start time    : Jun  1 2004  3:30:07:197PM
SID           : 0x010500000000000515000000a065cf7e784b9b5fe77c87709e611500
DBCC execution completed. If DBCC printed error messages, contact your system administrator.
```
  
> [!NOTE]  
>  Результат «UID (идентификатор пользователя)» не имеет смысла и будет удален в следующих версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
### <a name="b-specifying-the-with-tableresults-option"></a>Б. Указание параметра WITH TABLERESULTS  
В следующем примере результаты команды DBCC OPENTRAN загружаются во временную таблицу.
  
```sql  
-- Create the temporary table to accept the results.  
CREATE TABLE #OpenTranStatus (  
   ActiveTransaction varchar(25),  
   Details sql_variant   
   );  
-- Execute the command, putting the results in the table.  
INSERT INTO #OpenTranStatus   
   EXEC ('DBCC OPENTRAN WITH TABLERESULTS, NO_INFOMSGS');  
  
-- Display the results.  
SELECT * FROM #OpenTranStatus;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
[BEGIN TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-transaction-transact-sql.md)  
[COMMIT TRANSACTION (Transact-SQL)](../../t-sql/language-elements/commit-transaction-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[DB_ID (Transact-SQL)](../../t-sql/functions/db-id-transact-sql.md)  
[ROLLBACK TRANSACTION (Transact-SQL)](../../t-sql/language-elements/rollback-transaction-transact-sql.md)
  
  

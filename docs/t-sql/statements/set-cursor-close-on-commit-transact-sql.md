---
title: "SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CURSOR_CLOSE_ON_COMMIT
- SET CURSOR_CLOSE_ON_COMMIT
- CURSOR_CLOSE_ON_COMMIT_TSQL
- SET_CURSOR_CLOSE_ON_COMMIT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- CURSOR_CLOSE_ON_COMMIT option
- transactions [SQL Server], cursors
- closing cursors
- cursors [SQL Server], closing
- SET CURSOR_CLOSE_ON_COMMIT statement
ms.assetid: 7b976154-98ce-4a06-bbae-7e59c34211f7
caps.latest.revision: 38
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: de736d329175fe44c8bf837a2a6ef0ca966666ee
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-cursorcloseoncommit-transact-sql"></a>SET CURSOR_CLOSE_ON_COMMIT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Управляет поведением инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] COMMIT TRANSACTION. Значение этого параметра по умолчанию равно OFF. Это означает, что сервер не закроет курсоры при подтверждении транзакции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET CURSOR_CLOSE_ON_COMMIT { ON | OFF }  
```  
  
## <a name="remarks"></a>Замечания  
 Если параметр SET CURSOR_CLOSE_ON_COMMIT имеет значение ON, все открытые курсоры закрываются при фиксации или откате в соответствии со стандартом ISO. Если параметр SET CURSOR_CLOSE_ON_COMMIT имеет значение OFF, при фиксации транзакции курсор не закрывается.  
  
> [!NOTE]  
>  Установка SET CURSOR_CLOSE_ON_COMMIT в ON не закроет открытые курсоры при откате, если откат применяется к savepoint_name из инструкции SAVE TRANSACTION.  
  
 Если SET CURSOR_CLOSE_ON_COMMIT имеет значение OFF, то инструкция ROLLBACK закрывает только открытые асинхронные курсоры, которые не были до конца заполнены. Курсоры STATIC или INSENSITIVE, открытые после того, как были произведены изменения, более не отражают текущее состояние данных, если совершен откат изменений.  
  
 SET CURSOR_CLOSE_ON_COMMIT управляет тем же самым поведением, что и параметр базы данных CURSOR_CLOSE_ON_COMMIT. Если CURSOR_CLOSE_ON_COMMIT установлен в ON или OFF, то эта установка используется при соединении. Если SET CURSOR_CLOSE_ON_COMMIT не был указан, значение в **is_cursor_close_on_commit_on** столбца в **sys.databases** применяется представления каталога.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Собственного клиента OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента устанавливают параметр CURSOR_CLOSE_ON_COMMIT в значение OFF при подключении. Библиотека DB-Library автоматически не устанавливает значения CURSOR_CLOSE_ON_COMMIT.  
  
 Если параметр SET ANSI_DEFAULTS равно ON, включается SET CURSOR_CLOSE_ON_COMMIT.  
  
 Установка значения SET CURSOR_CLOSE_ON_COMMIT производится во время исполнения или запуска, но не во время синтаксического анализа.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @CURSOR_CLOSE VARCHAR(3) = 'OFF';  
IF ( (4 & @@OPTIONS) = 4 ) SET @CURSOR_CLOSE = 'ON';  
SELECT @CURSOR_CLOSE AS CURSOR_CLOSE_ON_COMMIT;  
```  
  
## <a name="permissions"></a>Permissions  
 Необходимо быть членом роли **public** .  
  
## <a name="examples"></a>Примеры  
 Следующий пример определяет курсор в транзакции и пытается использовать его после того, как транзакция зафиксирована.  
  
```  
-- SET CURSOR_CLOSE_ON_COMMIT  
-------------------------------------------------------------------------------  
SET NOCOUNT ON;  
  
CREATE TABLE t1 (a INT);  
GO   
  
INSERT INTO t1   
VALUES (1), (2);  
GO  
  
PRINT '-- SET CURSOR_CLOSE_ON_COMMIT ON';  
GO  
SET CURSOR_CLOSE_ON_COMMIT ON;  
GO  
PRINT '-- BEGIN TRAN';  
BEGIN TRAN;  
PRINT '-- Declare and open cursor';  
DECLARE testcursor CURSOR FOR  
    SELECT a FROM t1;  
OPEN testcursor;  
PRINT '-- Commit tran';  
COMMIT TRAN;  
PRINT '-- Try to use cursor';  
FETCH NEXT FROM testcursor;  
CLOSE testcursor;  
DEALLOCATE testcursor;  
GO  
PRINT '-- SET CURSOR_CLOSE_ON_COMMIT OFF';  
GO  
SET CURSOR_CLOSE_ON_COMMIT OFF;  
GO  
PRINT '-- BEGIN TRAN';  
BEGIN TRAN;  
PRINT '-- Declare and open cursor';  
DECLARE testcursor CURSOR FOR  
    SELECT a FROM t1;  
OPEN testcursor;  
PRINT '-- Commit tran';  
COMMIT TRAN;  
PRINT '-- Try to use cursor';  
FETCH NEXT FROM testcursor;  
CLOSE testcursor;  
DEALLOCATE testcursor;  
GO  
DROP TABLE t1;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [BEGIN TRANSACTION (Transact-SQL)](../../t-sql/language-elements/begin-transaction-transact-sql.md)   
 [ЗАКРЫТЬ &#40; Transact-SQL &#41;](../../t-sql/language-elements/close-transact-sql.md)   
 [COMMIT TRANSACTION (Transact-SQL)](../../t-sql/language-elements/commit-transaction-transact-sql.md)   
 [ROLLBACK TRANSACTION (Transact-SQL)](../../t-sql/language-elements/rollback-transaction-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)  
  
  


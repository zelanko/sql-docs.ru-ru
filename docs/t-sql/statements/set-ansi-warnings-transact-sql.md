---
title: "Параметр SET ANSI_WARNINGS (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET ANSI_WARNINGS
- ANSI_WARNINGS_TSQL
- ANSI_WARNINGS
- SET_ANSI_WARNINGS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], ISO standard behavior
- warnings [SQL Server]
- SET ANSI_WARNINGS statement
- ANSI_WARNINGS option
ms.assetid: f82aaab0-334f-427b-89b0-de4af596b4fa
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: feee804808cb9ba8d6e3dd97fb512a3a73301e17
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="set-ansiwarnings-transact-sql"></a>SET ANSI_WARNINGS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Задает поведение в соответствии со стандартом ISO для некоторых условий ошибок.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_WARNINGS { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_WARNINGS ON;  
```  
  
## <a name="remarks"></a>Замечания  
 Инструкция SET ANSI_WARNINGS влияет на следующие условия.  
  
-   Если значения NULL появляются в агрегатных функциях, таких как SUM, AVG, MAX, MIN, STDEV, STDEVP, VAR, VARP или COUNT, то при установке значения ON формируется предупреждающее сообщение. При установке значения OFF предупреждения не формируются.  
  
-   Если задано значение ON, то для инструкции, выполнение которой привело к ошибке деления на ноль или арифметического переполнения, будет выполнен откат и сформировано сообщение об ошибке. Если установлено значение OFF, то ошибки деления на ноль и арифметического переполнения приведут к возврату значений NULL. Возникает в которой ошибки деления на ноль и арифметического переполнения приводят возвращается значение null, если инструкция INSERT или UPDATE выполняется над **символ**, Юникод, или **двоичных** столбец, в котором длина нового значения превышает максимальный размер столбца. Если значение SET ANSI_WARNINGS установлено в ON, то выполнение инструкции INSERT или UPDATE прекращается в соответствии со стандартом ISO. Конечные пробелы игнорируются для символьных столбцов, а конечные значения NULL игнорируются для бинарных столбцов. Если указано значение OFF, то данные усекаются до размера столбца, и инструкция успешно завершается.  
  
    > [!NOTE]  
    >  Если усечение возникает во время преобразования в **двоичных** или **varbinary** выдан данных без предупреждения или ошибки, независимо от параметров SET.  
  
    > [!NOTE]  
    >  Значение ANSI_WARNINGS игнорируется при передаче аргументов хранимой процедуре или пользовательской функции, а также при объявлении и настройке переменных в инструкции пакетных заданий. Например, если переменная определена как **char(3)**и присвоено значение длиннее трех символов, данные будут усечены до определенного размера, а операция вставки или обновления инструкция была выполнена успешно.  
  
 Можно использовать параметр user options процедуры sp_configure для установки параметра ANSI_WARNINGS в значение по умолчанию для всех соединений с сервером. Дополнительные сведения см. в подразделе [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md).  
  
 Параметр SET ANSI_WARNINGS должен иметь значение ON при создании или изменении индексов, основанных на вычисляемых столбцах или индексированных представлениях. Если параметр SET ANSI_WARNINGS установлен в значение OFF, то выполнение инструкций CREATE, UPDATE, INSERT и DELETE на таблицах с индексами, основанными на вычисляемых столбцах или на индексированных представлениях, будет завершаться ошибкой. Дополнительные сведения о необходимых УСТАНОВКАХ параметров SET для индексированных представлений и индексов на вычисляемых столбцах см. в разделе «Вопросы при вы использования операторов SET» в [инструкции SET &#40; Transact-SQL &#41; ](../../t-sql/statements/set-statements-transact-sql.md).  
  
 В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] существует параметр базы данных ANSI_WARNINGS. Он эквивалентен параметру SET ANSI_WARNINGS. Если параметр SET ANSI_WARNINGS установлен в ON, то ошибки или предупреждения возникают при делении на ноль, в слишком больших строках для столбца базы данных и других подобных ошибках. Если SET ANSI_WARNINGS установлено в OFF, то эти ошибки и предупреждения не возникают. Значение по умолчанию в базе данных model для параметра SET ANSI_WARNINGS равно OFF. Если параметр не указан, то применяется значение параметра ANSI_WARNINGS. Если параметр SET ANSI_WARNINGS равно OFF, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использует значение столбца is_ansi_null_default_on в [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) представления каталога.  
  
 Параметр ANSI_WARNINGS должен быть установлен в ON для выполнения распределенных запросов.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента OLE DB для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при соединении автоматически устанавливают параметр ANSI_WARNINGS ON. Его можно настроить в источниках данных ODBC, в атрибутах соединения ODBC или в приложении перед сеансом связи. Для соединений от приложений DB-Library значение по умолчанию для параметра SET ANSI_WARNINGS равно значению OFF.  
  
 Если параметр SET ANSI_DEFAULTS установлен в ON, параметр SET ANSI_WARNINGS включен.  
  
 Параметр SET ANSI_WARNINGS устанавливается во время выполнения, а не во время синтаксического анализа.  
  
 Если один из параметров SET ARITHABORT или SET ARITHIGNORE установлен в значение OFF, а параметр SET ANSI_WARNINGS — в значение ON, то [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] возвращает сообщение об ошибке при обнаружении ошибок деления на ноль или переполнения.  
  
 Чтобы просмотреть текущее значение параметра для этого параметра, выполните следующий запрос.  
  
```  
DECLARE @ANSI_WARN VARCHAR(3) = 'OFF';  
IF ( (8 & @@OPTIONS) = 8 ) SET @ANSI_WARN = 'ON';  
SELECT @ANSI_WARN AS ANSI_WARNINGS;  
```  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 Следующий пример демонстрирует три рассмотренные ситуации со значениями ON и OFF для параметра SET ANSI_WARNINGS.  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE T1   
(  
   a int,   
   b int NULL,   
   c varchar(20)  
);  
GO  
  
SET NOCOUNT ON;  
  
INSERT INTO T1   
VALUES (1, NULL, '')   
      ,(1, 0, '')  
      ,(2, 1, '')  
      ,(2, 2, '');  
  
SET NOCOUNT OFF;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS ON';  
GO  
  
SET ANSI_WARNINGS ON;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (3, 3, 'Text string longer than 20 characters');  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS OFF';  
GO  
SET ANSI_WARNINGS OFF;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (4, 4, 'Text string longer than 20 characters');  
GO  
SELECT a, b, c   
FROM T1  
WHERE a = 4;  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
DROP TABLE T1  
```  
  
## <a name="see-also"></a>См. также:  
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [Инструкции SET (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS &#40; Transact-SQL &#41;](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [SESSIONPROPERTY &#40; Transact-SQL &#41;](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  


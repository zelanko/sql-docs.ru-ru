---
title: "IDENTITY (свойство) (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IDENTITY_TSQL
- IDENTITY
dev_langs:
- TSQL
helpviewer_keywords:
- IDENTITY property
- columns [SQL Server], creating
- identity columns [SQL Server], IDENTITY property
- autonumbers, identity numbers
ms.assetid: 8429134f-c821-4033-a07c-f782a48d501c
caps.latest.revision: 27
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1eb7f960210ec89a66f1307d8476e6d47494861f
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="create-table-transact-sql-identity-property"></a>Создание таблицы (Transact-SQL) IDENTITY (свойство)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md.md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  Создает в таблице столбец идентификаторов. Это свойство указывается в инструкциях языка [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TABLE и ALTER TABLE.  
  
> [!NOTE]  
>  Свойство IDENTITY отличается от SQL-DMO **удостоверение** свойство, которое предоставляет доступ к свойству идентификаторов строк столбца.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
IDENTITY [ (seed , increment) ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *Начальное значение*  
 Значение, присваиваемое самой первой строке, загружаемой в таблицу.  
  
 *приращение*  
 Значение приращения, которое прибавляется к значению идентификатора предыдущей загруженной строки.  
  
 Необходимо указывать либо оба аргумента (и seed, и increment), либо не указывать ни одного из них. Если ничего не указано, применяется значение по умолчанию (1,1).  
  
## <a name="remarks"></a>Замечания  
 Столбцы идентификаторов можно использовать для формирования значений ключей. Свойство идентификаторов столбца гарантирует следующее.  
  
-   Каждое новое значение будет сформировано на основе текущих аргументов seed и increment.  
  
-   Каждое новое значение для определенной транзакции будет отлично от других параллельных транзакций для таблицы.  
  
 Свойство идентификаторов столбца не гарантирует следующее.  
  
-   **Уникальность значения** — уникальность следует обеспечивать с помощью **ПЕРВИЧНОГО ключа** или **UNIQUE** ограничение или **UNIQUE** индекса.  
  
-   **Последовательные значения в пределах транзакции** – транзакции вставки нескольких строк для получения последовательные значения строки, так как может произойти другие параллельные операции вставки для таблицы не гарантируется. Если значения должны быть последовательными, то транзакции необходимо использовать монопольную блокировку для таблицы или **SERIALIZABLE** уровень изоляции.  
  
-   **Последовательные значения после перезапуска сервера или другого сбоя** —[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может кэшировать значения идентификаторов для повышения производительности и некоторые из присвоенных значений могут быть потеряны во время перезапуска сбоя или сервера базы данных. Это может вызвать пропуски в значениях идентификатора при вставке. Если пропуски недопустимы, приложение должно использовать собственный механизм для создания значений ключей. Использование генератора последовательностей с **NOCACHE** может привести к ограничению пропусков в неподтвержденных транзакциях.  
  
-   **Повторное использование значений** — для свойства указанному идентификатору с определенной аргументами seed и increment, удостоверение, не используются повторно подсистемой. Если определенная инструкция вставки завершается с ошибкой или производится ее откат, использованные значения идентификаторов не будут созданы повторно. Это может привести к появлению пропусков при создании последующих значений идентификаторов.  
  
 Эти ограничения были созданы намеренно и предназначены для повышения производительности, поскольку они являются допустимыми во многих типичных ситуациях. Если из-за этих ограничений невозможно использовать значения идентификаторов, рекомендуется создать отдельную таблицу, содержащую текущее значение, управление доступом к которой и назначение чисел будет выполняться приложением.  
  
 Если таблица со столбцом идентификаторов опубликована для репликации, этот столбец должен обслуживаться в соответствии с типом репликации. Дополнительные сведения см. в статье [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md).  
  
 Для каждой таблицы можно создать только один столбец идентификаторов.  
  
 В таблицах, оптимизированных для памяти, в качестве начального значения и значения приращения должно быть задано 1,1. Установка начального значения или приращения значение, отличное от 1 приведет к следующей ошибке: использование начального значения и приращения другие значения 1 не поддерживается с таблицами, оптимизированными для памяти.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-using-the-identity-property-with-create-table"></a>A. Свойство IDENTITY в инструкции CREATE TABLE  
 В следующем примере производится создание новой таблицы со свойством `IDENTITY` для получения автоматически увеличивающегося идентификационного номера.  
  
```  
USE AdventureWorks2012;  
  
IF OBJECT_ID ('dbo.new_employees', 'U') IS NOT NULL  
   DROP TABLE new_employees;  
GO  
CREATE TABLE new_employees  
(  
 id_num int IDENTITY(1,1),  
 fname varchar (20),  
 minit char(1),  
 lname varchar(30)  
);  
  
INSERT new_employees  
   (fname, minit, lname)  
VALUES  
   ('Karin', 'F', 'Josephs');  
  
INSERT new_employees  
   (fname, minit, lname)  
VALUES  
   ('Pirkko', 'O', 'Koskitalo');  
```  
  
### <a name="b-using-generic-syntax-for-finding-gaps-in-identity-values"></a>Б. Базовый синтаксис для поиска промежутков в нумерации идентификаторов  
 Следующий пример демонстрирует базовый синтаксис для поиска разрывов в нумерации идентификаторов, возникающих при удалении данных.  
  
> [!NOTE]  
>  Первая часть данного скрипта [!INCLUDE[tsql](../../includes/tsql-md.md)] приведена только в учебных целях. Можно запустить [!INCLUDE[tsql](../../includes/tsql-md.md)] сценарий, начиная с комментария: `-- Create the img table`.  
  
```  
-- Here is the generic syntax for finding identity value gaps in data.  
-- The illustrative example starts here.  
SET IDENTITY_INSERT tablename ON;  
DECLARE @minidentval column_type;  
DECLARE @maxidentval column_type;  
DECLARE @nextidentval column_type;  
SELECT @minidentval = MIN($IDENTITY), @maxidentval = MAX($IDENTITY)  
    FROM tablename  
IF @minidentval = IDENT_SEED('tablename')  
   SELECT @nextidentval = MIN($IDENTITY) + IDENT_INCR('tablename')  
   FROM tablename t1  
   WHERE $IDENTITY BETWEEN IDENT_SEED('tablename') AND   
      @maxidentval AND  
      NOT EXISTS (SELECT * FROM tablename t2  
         WHERE t2.$IDENTITY = t1.$IDENTITY +   
            IDENT_INCR('tablename'))  
ELSE  
   SELECT @nextidentval = IDENT_SEED('tablename');  
SET IDENTITY_INSERT tablename OFF;  
-- Here is an example to find gaps in the actual data.  
-- The table is called img and has two columns: the first column   
-- called id_num, which is an increasing identification number, and the   
-- second column called company_name.  
-- This is the end of the illustration example.  
  
-- Create the img table.  
-- If the img table already exists, drop it.  
-- Create the img table.  
IF OBJECT_ID ('dbo.img', 'U') IS NOT NULL  
   DROP TABLE img;  
GO  
CREATE TABLE img (id_num int IDENTITY(1,1), company_name sysname);  
INSERT img(company_name) VALUES ('New Moon Books');  
INSERT img(company_name) VALUES ('Lucerne Publishing');  
-- SET IDENTITY_INSERT ON and use in img table.  
SET IDENTITY_INSERT img ON;  
  
DECLARE @minidentval smallint;  
DECLARE @nextidentval smallint;  
SELECT @minidentval = MIN($IDENTITY) FROM img  
 IF @minidentval = IDENT_SEED('img')  
    SELECT @nextidentval = MIN($IDENTITY) + IDENT_INCR('img')  
    FROM img t1  
    WHERE $IDENTITY BETWEEN IDENT_SEED('img') AND 32766 AND  
      NOT    EXISTS (SELECT * FROM img t2  
          WHERE t2.$IDENTITY = t1.$IDENTITY + IDENT_INCR('img'))  
 ELSE  
    SELECT @nextidentval = IDENT_SEED('img');  
SET IDENTITY_INSERT img OFF;  
```  
  
## <a name="see-also"></a>См. также:  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DBCC CHECKIDENT (Transact-SQL)](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [IDENT_INCR &#40; Transact-SQL &#41;](../../t-sql/functions/ident-incr-transact-sql.md)   
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)   
 [УДОСТОВЕРЕНИЕ &#40; Функция &#41; &#40; Transact-SQL &#41;](../../t-sql/functions/identity-function-transact-sql.md)   
 [IDENT_SEED &#40; Transact-SQL &#41;](../../t-sql/functions/ident-seed-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [SET IDENTITY_INSERT &#40; Transact-SQL &#41;](../../t-sql/statements/set-identity-insert-transact-sql.md)   
 [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  

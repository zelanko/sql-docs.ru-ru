---
title: "@@IDENTITY (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 08/29/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '@@IDENTITY_TSQL'
- '@@IDENTITY'
dev_langs:
- TSQL
helpviewer_keywords:
- last-inserted identity values
- identity values [SQL Server], last-inserted
- '@@IDENTITY function'
ms.assetid: 912e4485-683c-41c2-97b3-8831c0289ee4
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 88cdaa1362e5d60b0f880c66c7fb7038ddb9f126
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="x40x40identity-transact-sql"></a>&#x40;&#x40; УДОСТОВЕРЕНИЕ (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Системная функция, которая возвращает значение идентификатора, вставленное последним.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@IDENTITY  
```  
  
## <a name="return-types"></a>Типы возвращаемых значений  
 **numeric(38,0)**  
  
## <a name="remarks"></a>Замечания  
 После инструкции INSERT, SELECT INTO или массового копирования будет закончена, @@IDENTITY содержит последнее значение идентификатора, сформированное инструкцией. Если инструкция не обработала все таблицы со столбцами идентификаторов@IDENTITY возвращает значение NULL. При вставке нескольких строк, формируется несколько значений идентификаторов, @@IDENTITY возвращает последнее созданное значение идентификатора. Если в результате инструкции срабатывает один или несколько триггеров, которые выполняют вставки, формирующие значения идентификаторов, при вызове@IDENTITY сразу после инструкции возвращает последнее значение идентификатора, сформированное триггерами. Если триггер срабатывает после выполнения вставки в таблицу со столбцом идентификаторов и триггер производит вставку в другую таблицу, которая имеет столбец идентификаторов @@IDENTITY возвращает значение идентификатора первой вставки. @@IDENTITY Значение не возвращается к предыдущей параметр, если инструкции INSERT, SELECT INTO или массового копирования завершается сбоем, или откат транзакции.  
  
 Неудачно завершившиеся инструкции и транзакции могут изменить текущий идентификатор таблицы и создать пропуски в значениях столбца идентификаторов. Для значения идентификатора никогда не производится откат, несмотря на то, что транзакция, пытавшаяся вставить в таблицу значение, не была зафиксирована. Например, если инструкция INSERT привела к ошибке из-за нарушения ограничения IGNORE_DUP_KEY, текущее значение идентификатора для таблицы все равно увеличивается.  
  
 @@IDENTITY, SCOPE_IDENTITY и IDENT_CURRENT, аналогичные функции, поскольку все они возвращают последнее значение, вставленное в столбец ИДЕНТИФИКАТОРОВ таблицы.  
  
 @@IDENTITY и SCOPE_IDENTITY возвращают последнее значение идентификатора, сформированное в любой таблице в текущем сеансе. Однако функция SCOPE_IDENTITY возвращает значение только в пределах текущей области; @@IDENTITY не ограничена определенной области.  
  
 Функция IDENT_CURRENT не ограничена областью действия и сеансом, но ограничена указанной таблицей. Функция IDENT_CURRENT возвращает значение идентификатора, сформированное для определенной таблицы в любом сеансе и в любой области. Дополнительные сведения см. в разделе [IDENT_CURRENT &#40; Transact-SQL &#41; ](../../t-sql/functions/ident-current-transact-sql.md).  
  
 Область @@IDENTITY функция является текущий сеанс на локальном сервере, на котором он выполняется. Эту функцию невозможно применить к удаленным или связанным серверам. Чтобы получить значение идентификатора на другом сервере, выполните хранимую процедуру на удаленном или связанном сервере и используйте эту хранимую процедуру (которая выполняется в контексте удаленного или связанного сервера) для сбора значения идентификатора и его возврата вызывающему соединению на локальном сервере.  
  
 Репликация может затронуть @@IDENTITY значение, так как он используется в репликации триггеры и хранимые процедуры. @@IDENTITY не является надежным признаком последнего созданного пользователем идентификатора, если столбец является частью статьи репликации. Можно использовать функцию SCOPE_IDENTITY() вместо @@IDENTITY. Дополнительные сведения см. в разделе [SCOPE_IDENTITY &#40; Transact-SQL &#41;](../../t-sql/functions/scope-identity-transact-sql.md)  
  
> [!NOTE]  
>  Вызов хранимой процедуры или [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции должны быть переписаны для использования `SCOPE_IDENTITY()` функции, которая возвращает последний идентификатор, использованный в области этой пользовательской инструкции, а не идентификатор в области вложенного триггера, используемого репликация.  
  
## <a name="examples"></a>Примеры  
 Следующий пример вставляет строку в таблицу, содержащую столбец идентификаторов (`LocationID`), и применяет функцию `@@IDENTITY` для отображения значения идентификатора, используемого в новой строке.  
  
```  
USE AdventureWorks2012;  
GO  
--Display the value of LocationID in the last row in the table.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
INSERT INTO Production.Location (Name, CostRate, Availability, ModifiedDate)  
VALUES ('Damaged Goods', 5, 2.5, GETDATE());  
GO  
SELECT @@IDENTITY AS 'Identity';  
GO  
--Display the value of LocationID of the newly inserted row.  
SELECT MAX(LocationID) FROM Production.Location;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENT_CURRENT (Transact-SQL)](../../t-sql/functions/ident-current-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [SCOPE_IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/scope-identity-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  


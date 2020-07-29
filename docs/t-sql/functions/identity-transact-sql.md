---
title: '@@IDENTITY (Transact-SQL) | Документы Майкрософт'
ms.custom: ''
ms.date: 08/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
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
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: d5a41eec147978e3e794c77e4c79336daa780e29
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87113435"
---
# <a name="x40x40identity-transact-sql"></a>&#x40;&#x40;IDENTITY (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Системная функция, которая возвращает значение идентификатора, вставленное последним.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
@@IDENTITY  
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="return-types"></a>Типы возвращаемых данных
 **numeric(38,0)**  
  
## <a name="remarks"></a>Remarks  
 После выполнения инструкций INSERT, SELECT INTO или массового копирования функция @@IDENTITY возвращает последнее значение идентификатора, сформированное инструкцией. Если инструкция не обработала ни одной таблицы, содержащей столбцы идентификаторов, функция @@IDENTITY возвращает значение NULL. Если при вставке нескольких строк формируется несколько значений идентификаторов, функция @@IDENTITY возвращает последнее сформированное значение. Если в результате инструкции срабатывает один или несколько триггеров, которые выполняют вставки, формирующие значения идентификаторов, вызов функции @@IDENTITY сразу же после завершения инструкции возвращает последнее значение идентификатора, сформированное триггерами. Если триггер срабатывает после выполнения вставки в таблицу, содержащую столбец идентификаторов, и триггер производит вставку в другую таблицу, в которой не содержится столбец идентификаторов, функция @@IDENTITY возвращает значение идентификатора первой вставки. Предыдущее значение @@IDENTITY не восстанавливается, если инструкция INSERT, SELECT INTO или массового копирования завершились ошибкой либо если выполняется откат транзакции.  
  
 Неудачно завершившиеся инструкции и транзакции могут изменить текущий идентификатор таблицы и создать пропуски в значениях столбца идентификаторов. Для значения идентификатора никогда не производится откат, несмотря на то, что транзакция, пытавшаяся вставить в таблицу значение, не была зафиксирована. Например, если инструкция INSERT привела к ошибке из-за нарушения ограничения IGNORE_DUP_KEY, текущее значение идентификатора для таблицы все равно увеличивается.  
  
 Функции @@IDENTITY, SCOPE_IDENTITY и IDENT_CURRENT похожи, так как все они возвращают последнее значение, вставленное в столбец IDENTITY таблицы.  
  
 Функции @@IDENTITY и SCOPE_IDENTITY возвращают последнее значение идентификатора, сформированное в любой таблице в текущем сеансе. Однако функция SCOPE_IDENTITY возвращает значение только в пределах текущей области, в то время как функция @@IDENTITY не ограничена определенной областью.  
  
 Функция IDENT_CURRENT не ограничена областью действия и сеансом, но ограничена указанной таблицей. Функция IDENT_CURRENT возвращает значение идентификатора, сформированное для определенной таблицы в любом сеансе и в любой области. Дополнительные сведения см. в статье [IDENT_CURRENT (Transact-SQL)](../../t-sql/functions/ident-current-transact-sql.md).  
  
 Областью функции @@IDENTITY является текущий сеанс на локальном сервере, на котором она выполняется. Эту функцию невозможно применить к удаленным или связанным серверам. Чтобы получить значение идентификатора на другом сервере, выполните хранимую процедуру на удаленном или связанном сервере и используйте эту хранимую процедуру (которая выполняется в контексте удаленного или связанного сервера) для сбора значения идентификатора и его возврата вызывающему соединению на локальном сервере.  
  
 Репликация может затронуть значение системной переменной @@IDENTITY, так как она используется в триггерах и хранимых процедурах репликации. Функция @@IDENTITY не является надежным признаком последнего созданного пользователем идентификатора, если столбец является частью статьи репликации. Вместо @@IDENTITY можно использовать функцию SCOPE_IDENTITY(). Дополнительные сведения см. в статье [SCOPE_IDENTITY (Transact-SQL)](../../t-sql/functions/scope-identity-transact-sql.md).  
  
> [!NOTE]  
>  Вызывающая хранимая процедура или инструкция [!INCLUDE[tsql](../../includes/tsql-md.md)] должны быть переписаны, чтобы использовать функцию `SCOPE_IDENTITY()`, которая возвращает последний идентификатор, использованный в области этой пользовательской инструкции, а не идентификатор, относящийся к области вложенного триггера, используемого репликацией.  
  
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
 [Системные функции (Transact-SQL)](../../relational-databases/system-functions/system-functions-category-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [IDENT_CURRENT (Transact-SQL)](../../t-sql/functions/ident-current-transact-sql.md)   
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [SCOPE_IDENTITY (Transact-SQL)](../../t-sql/functions/scope-identity-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  

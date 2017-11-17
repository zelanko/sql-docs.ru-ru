---
title: "ALTER PARTITION FUNCTION (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER PARTITION FUNCTION
- ALTER_PARTITION_FUNCTION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- splitting partitions [SQL Server]
- partitioned tables [SQL Server], splitting
- ALTER PARTITION FUNCTION statement
- merging partitions [SQL Server]
- partitioned indexes [SQL Server], merging
- partitioned indexes [SQL Server], splitting
- modifying partition functions
- partition functions [SQL Server], modifying
- partitioned tables [SQL Server], merging
ms.assetid: 70866dac-0a8f-4235-8108-51547949ada4
caps.latest.revision: 43
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5969f9487a55437febfba9f6deec7fb1e0df5f02
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="alter-partition-function-transact-sql"></a>ALTER PARTITION FUNCTION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Эта инструкция изменяет функцию секционирования путем разбиения или слияния ее пограничных значений. При выполнении инструкции ALTER PARTITION FUNCTION одна секция какой-либо таблицы или индекса, которые используют функцию секционирования, может быть разбита на две секции или две секции могут быть объединены в одну.  
  
> [!CAUTION]  
>  Несколько таблиц или индексов могут использовать одинаковую функцию секционирования. Инструкция ALTER PARTITION FUNCTION применяется ко всем таблицам и индексам в рамках одной транзакции.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
ALTER PARTITION FUNCTION partition_function_name()  
{   
    SPLIT RANGE ( boundary_value )  
  | MERGE RANGE ( boundary_value )   
} [ ; ]  
```  
  
## <a name="arguments"></a>Аргументы  
 *partition_function_name*  
 Это имя функции секционирования, которую необходимо изменить.  
  
 SPLIT RANGE ( *boundary_value* )  
 Добавляет одну секцию к функции секционирования. *boundary_value* определяет диапазон новой секции, который должен отличаться от существующих пограничных значений функции секционирования. На основе *boundary_value*, [!INCLUDE[ssDE](../../includes/ssde-md.md)] разбивает один существующий диапазон на два. Эти два том, в котором новый *boundary_value* находится считается новой секции.  
  
 Файловая группа должна существовать в режиме в сети и быть помеченной схемой секционирования, использующей функцию секционирования, как NEXT USED для сохранения новой секции. В инструкции CREATE PARTITION SCHEME для файловых групп выделяются секции. Если инструкция CREATE PARTITION SCHEME размещает больше файловых групп, чем необходимо (в этой инструкции создано меньше секций, чем файловых групп для их хранения), то появляются неназначенные файловые группы, и одна из них отмечается схемой секционирования как NEXT USED. Данная файловая группа будет содержать новую секцию. Если нет ни одной файловой группы, отмеченной схемой секционирования как NEXT USED, то для хранения новой секции необходимо добавить файловую группу или назначить уже существующую при помощи инструкции ALTER PARTITION SCHEME. Файловая группа, которая уже содержит секции, может быть назначена для содержания дополнительных секций. Так как функция секционирования может использоваться в нескольких схемах секционирования, то все схемы с такой функцией, к которым добавляются секции, должны иметь файловую группу NEXT USED. Иначе ALTER PARTITION FUNCTION дает сбой, и выдает ошибку, в которой показаны схема или схемы секционирования с отсутствующей файловой группой NEXT USED.  
  
 Если все секции создаются в одной файловой группе, то данная группа первоначально автоматически назначается как NEXT USED. Однако после выполнения операции разбиения назначенная файловая группа NEXT USED будет отсутствовать. Необходимо явным образом назначить файловую группу NEXT USED с помощью ALTER PARITION SCHEME, в противном случае следующая операция разбиения завершится ошибкой.  
  
> [!NOTE]  
>  Ограничения с индексом columnstore: только пустые секции могут быть разбиты, если в таблице существует индекс columnstore. Будет необходимо удалить или отключить индекс columnstore перед выполнением этой операции  
  
 ОБЪЕДИНЕНИЕ [ДИАПАЗОНА ( *boundary_value*)]  
 Удаляет секцию и объединяет все значения, существующие в секции, в одну из оставшихся. ДИАПАЗОН (*boundary_value*) должен быть существующим пограничным значением, в которое объединяются значения из удаленной секции. Файловая группа, изначально содержащая *boundary_value* удаляется из схемы секционирования, если она используется оставшейся секцией или помечается свойство NEXT USED. Объединенная секция находится в файловой группе, которая изначально не содержит *boundary_value*. *boundary_value* — это константное выражение, которое может ссылаться на переменные (включая определяемый пользователем тип переменных) или функции (включая определяемые пользователем функции). Не может ссылаться на выражение [!INCLUDE[tsql](../../includes/tsql-md.md)]. *boundary_value* должны либо соответствовать или неявно преобразовываться в тип данных соответствующего столбца секционирования и не может быть усечен во время неявного преобразования таким образом, размер и масштаб значения не совпадали с его соответствующий *input_parameter_type*.  
  
> [!NOTE]  
>  Ограничения с индексом columnstore: не удалось выполнить слияние двух непустых секций, содержащих индекс columnstore. Будет необходимо удалить или отключить индекс columnstore перед выполнением этой операции  
  
## <a name="best-practices"></a>Рекомендации  
 Всегда оставляйте пустые секции в начале и в конце диапазона секций, чтобы гарантировать отсутствие любого перемещения данных при разбиении секций (до загрузки новых данных) и их объединении (после выгрузки старых данных). Избегайте разбиения или слияния заполненных секций. Это может привести к существенному снижению производительности, поскольку может увеличить время формирования журнала в четыре раза, а также вызвать блокировку.  
  
## <a name="limitations-and-restrictions"></a>Ограничения  
 Инструкция ALTER PARTITION FUNCTION повторно секционирует все таблицы и индексы, которые применяют функцию в рамках одной атомной операции. Однако данная операция происходит в режиме вне сети и, в зависимости от масштаба повторного секционирования, может потребовать большого количества ресурсов.  
  
 Инструкция ALTER PARTITION FUNCTION может использоваться только для разбиения одной секции на две или слияния двух секций в одну. Чтобы разбить таблицу другим способом (например, от 10 секций до 5), можно использовать следующие параметры. В зависимости от конфигурации системы данные параметры могут различаться по ресурсоемкости.  
  
-   Создайте новую секционированную таблицу с необходимой функцией секционирования, затем вставьте данные из старой таблицы в новую при помощи инструкции INSERT INTO...SELECT FROM.  
  
-   Создайте секционированный кластеризованный индекс по всей куче.  
  
    > [!NOTE]  
    >  Удаление результатов секционированного кластеризованного индекса в секционированной куче.  
  
-   Удалите и заново создайте существующий секционированный индекс с помощью инструкции [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE INDEX с предложением DROP EXISTING = ON.  
  
-   Выполните последовательность инструкций ALTER PARTITION FUNCTION.  
  
 Все файловые группы, обрабатываемые ALTER PARITITION FUNCTION, должны находиться в режиме в сети.  
  
 ALTER PARTITION FUNCTION завершается неудачно, если в какой-либо таблице, использующей функцию секционирования, находится отключенный кластеризованный индекс.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает репликацию для изменения функций секционирования. Изменения в функции секционирования в базе данных публикации нужно вручную применять к базе данных подписки.  
  
## <a name="permissions"></a>Permissions  
 Для выполнения инструкции ALTER PARTITION FUNCTION может использоваться одно из перечисленных ниже разрешений.  
  
-   Разрешение ALTER ANY DATASPACE. Это разрешение назначено по умолчанию членам предопределенной роли сервера **sysadmin** и предопределенных ролей базы данных **db_owner** и **db_ddladmin** .  
  
-   Разрешение CONTROL или ALTER в базе данных, в которой была создана функция секционирования.  
  
-   Разрешение CONTROL SERVER или ALTER ANY DATABASE на сервере базы данных, в которой была создана функция секционирования.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-splitting-a-partition-of-a-partitioned-table-or-index-into-two-partitions"></a>A. Разбиение секции секционированной таблицы или индекса на две части  
 В следующем примере создается функция секционирования для разделения таблицы или индекса на четыре секции. `ALTER PARTITION FUNCTION` разбивает одну из секций на две, в результате получается пять секций.  
  
```tsql  
IF EXISTS (SELECT * FROM sys.partition_functions  
    WHERE name = 'myRangePF1')  
DROP PARTITION FUNCTION myRangePF1;  
GO  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
GO  
--Split the partition between boundary_values 100 and 1000  
--to create two partitions between boundary_values 100 and 500  
--and between boundary_values 500 and 1000.  
ALTER PARTITION FUNCTION myRangePF1 ()  
SPLIT RANGE (500);  
```  
  
### <a name="b-merging-two-partitions-of-a-partitioned-table-into-one-partition"></a>Б. Объединение двух секций секционированной таблицы в одну секцию  
 Следующий пример создает такую же функцию секционирования, как описано выше, и затем объединяет две секции в одну, чтобы в итоге получилось три секции.  
  
```tsql  
IF EXISTS (SELECT * FROM sys.partition_functions  
    WHERE name = 'myRangePF1')  
DROP PARTITION FUNCTION myRangePF1;  
GO  
CREATE PARTITION FUNCTION myRangePF1 (int)  
AS RANGE LEFT FOR VALUES ( 1, 100, 1000 );  
GO  
--Merge the partitions between boundary_values 1 and 100  
--and between boundary_values 100 and 1000 to create one partition  
--between boundary_values 1 and 1000.  
ALTER PARTITION FUNCTION myRangePF1 ()  
MERGE RANGE (100);  
```  
  
## <a name="see-also"></a>См. также:  
 [Секционированные таблицы и индексы](../../relational-databases/partitions/partitioned-tables-and-indexes.md)   
 [CREATE PARTITION FUNCTION (Transact-SQL)](../../t-sql/statements/create-partition-function-transact-sql.md)   
 [DROP PARTITION FUNCTION &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-function-transact-sql.md)   
 [CREATE PARTITION SCHEME (Transact-SQL)](../../t-sql/statements/create-partition-scheme-transact-sql.md)   
 [ALTER PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/alter-partition-scheme-transact-sql.md)   
 [DROP PARTITION SCHEME &#40; Transact-SQL &#41;](../../t-sql/statements/drop-partition-scheme-transact-sql.md)   
 [CREATE INDEX (Transact-SQL)](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX (Transact-SQL)](../../t-sql/statements/alter-index-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [sys.partition_functions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-functions-transact-sql.md)   
 [sys.partition_parameters &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-parameters-transact-sql.md)   
 [sys.partition_range_values &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partition-range-values-transact-sql.md)   
 [sys.partitions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md)   
 [sys.tables (Transact-SQL)](../../relational-databases/system-catalog-views/sys-tables-transact-sql.md)   
 [sys.indexes (Transact-SQL)](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns (Transact-SQL)](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  


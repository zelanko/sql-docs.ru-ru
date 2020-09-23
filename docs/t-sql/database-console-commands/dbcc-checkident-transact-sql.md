---
description: DBCC CHECKIDENT (Transact-SQL)
title: DBCC CHECKIDENT (Transact-SQL)
ms.custom: ''
ms.date: 03/07/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CHECKIDENT
- DBCC CHECKIDENT
- CHECKIDENT_TSQL
- DBCC_CHECKIDENT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- checking identity values
- reseeding identity values
- resetting identity values
- identity values [SQL Server]
- identity values [SQL Server], checking
- modifying identity values
- current identity values
- DBCC CHECKIDENT statement
- identity values [SQL Server], reseeding
- reporting current identity values
ms.assetid: 2c00ee51-2062-4e47-8b19-d90f524c6427
author: pmasl
ms.author: umajay
monikerRange: = azuresqldb-current || >= sql-server-2016 || >= sql-server-linux-2017 || = azure-sqldw-latest||= sqlallproducts-allversions
ms.openlocfilehash: a630e9d8d1622d10015c3c23024fa643f858bde0
ms.sourcegitcommit: 1126792200d3b26ad4c29be1f561cf36f2e82e13
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/14/2020
ms.locfileid: "90076675"
---
# <a name="dbcc-checkident-transact-sql"></a>DBCC CHECKIDENT (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

  Проверяет текущее значение идентификатора для указанной таблицы в [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и при необходимости изменяет его. Также инструкцию DBCC CHECKIDENT можно использовать для ручной установки нового текущего значения идентификатора для столбца идентификаторов.  
  
 ![Значок ссылки на статью](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на статью") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
-- Syntax for SQL Server and Azure SQL Database  

DBCC CHECKIDENT
 (
    table_name  
        [, { NORESEED | { RESEED [, new_reseed_value ] } } ]  
)  
[ WITH NO_INFOMSGS ]  
```  

```syntaxsql
-- Syntax for Azure Synapse Analytics
DBCC CHECKIDENT   
 (   
    table_name  
        [RESEED, new_reseed_value ]   
)  
[ WITH NO_INFOMSGS ]  
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы

 *table_name*  
 Это имя таблицы, для которой выполняется проверка текущего значения идентификатора. Указанная таблица должна содержать столбец идентификаторов. Имена таблиц должны соответствовать правилам для [идентификаторов](../../relational-databases/databases/database-identifiers.md). Имена из двух или трех частей должны содержать разделители, например "<Человек>.<Тип_адреса>" или [<Человек>.<Тип_адреса>].
  
 NORESEED  
 Указывает, что текущее значение идентификатора не должно изменяться.  
  
 RESEED  
 Определяет, что текущее значение идентификатора должно изменяться.  
  
 *new_reseed_value*  
 Новое значение, предназначенное для использования в качестве текущего значения для столбца идентификаторов.  
  
 WITH NO_INFOMSGS  
 Подавляет вывод всех информационных сообщений.  
  
## <a name="remarks"></a>Remarks

 Конкретные изменения, вносимые в текущее значение идентификатора, зависят от определений параметров.  
  
|команда DBCC CHECKIDENT|Изменение текущего значения идентификатора или идентификаторов|  
|-----------------------------|---------------------------------------------|  
|DBCC CHECKIDENT (*table_name*, NORESEED)|Текущее значение идентификатора не сбрасывается. Инструкция DBCC CHECKIDENT возвращает текущее значение идентификатора и текущее максимальное значение столбца идентификаторов. Если эти два значения не равны друг другу, необходимо сбросить значение идентификатора, чтобы избежать потенциальных ошибок или пропусков в последовательности значений.|  
|DBCC CHECKIDENT (*table_name*)<br /><br /> или диспетчер конфигурации служб<br /><br /> DBCC CHECKIDENT (*table_name*, RESEED)|Если текущее значение идентификатора таблицы меньше, чем максимальное значение из содержащихся в столбце, оно устанавливается в максимальное значение в столбце идентификаторов. См. раздел «Исключения» далее.|  
|DBCC CHECKIDENT (*table_name*, RESEED, *new_reseed_value*)|В качестве текущего значения идентификатора задается *new_reseed_value*. Если со времени создания таблицы в нее не вставлялись строки или все строки были удалены с помощью инструкции TRUNCATE TABL, то первая строка, вставляемая после запуска инструкции DBCC CHECKIDENT, будет использовать значение *new_reseed_value* в качестве идентификатора. Если в таблице есть строки или если все строки были удалены с помощью инструкции DELETE, следующая строка вставляется со значением *new_reseed_value* и [текущим шагом приращения](../../t-sql/functions/ident-incr-transact-sql.md). Если транзакция вставляет строку и впоследствии подверглась откату, то следующая вставленная строка использует *new_reseed_value* + [текущий шаг](../../t-sql/functions/ident-incr-transact-sql.md) значение так, как если бы строка была удалена. Если таблица не пустая, установка значения идентификатора меньше, чем максимальное значение столбца идентификаторов может привести к одному из следующих условий.<br /><br /> — Если в столбце идентификаторов существуют ограничения PRIMARY KEY или UNIQUE, при выполнении последующих операций вставки в таблицу будет сформировано сообщение об ошибке 2627, потому что созданное значение идентификатора будет конфликтовать с существующими значениями.<br /><br /> — Если ограничения PRIMARY KEY или UNIQUE отсутствуют, последующие операции вставки приведут к дублированию значений идентификаторов.|  
  
## <a name="exceptions"></a>Исключения

 В следующей таблице перечислены условия, при которых инструкция DBCC CHECKIDENT не будет выполнять автоматический сброс текущего значения идентификатора, а также представлены способы сброса значения.  
  
|Условие|Способы сброса|  
|---------------|-------------------|  
|Текущее значение идентификатора больше максимального значения в таблице.|Выполните инструкцию DBCC CHECKIDENT (*table_name*, NORESEED) чтобы определить текущее максимальное значение в столбце. Затем укажите это значение как *new_reseed_value* для команды DBCC CHECKIDENT (*table_name*, RESEED,*new_reseed_value*).<br /><br /> -или-<br /><br /> Выполните инструкцию DBCC CHECKIDENT (*table_name*, RESEED,*new_reseed_value*) с очень низким значением *new_reseed_value*, а затем выполните инструкцию DBCC CHECKIDENT (*table_name*, RESEED), чтобы исправить значение.|  
|Из таблицы удалены все строки.|Выполните инструкцию DBCC CHECKIDENT (*table_name*, RESEED,*new_reseed_value*) с новым начальным значением *new_reseed_value*.|  
  
## <a name="changing-the-seed-value"></a>Изменение начального значения

 Начальное значение представляет собой значение, вставляемое в столбец идентификаторов для первой строки, загружаемой в таблицу. Все последующие строки содержат текущее значение идентификатора, увеличенное на значение приращения, где текущее значение идентификатора представляет собой последнее значение идентификатора, сформированное для таблицы или представления.  
  
 Инструкцию DBCC CHECKIDENT нельзя использовать для следующих задач:  
  
- Изменение исходного начального значения, которое было указано для столбца идентификаторов при создании таблицы или представления.  
  
- Повторное указание начального значения для существующих строк в таблице или представлении.  
  
 Чтобы изменить исходное начальное значение и повторно задать начальное значение для каких-либо существующих строк, удалите столбец идентификаторов и создайте его повторно, указав новое начальное значение. Если таблица содержит данные, то номера идентификаторов добавляются к существующим строкам с учетом указанного начального значения и приращения. Порядок, в котором выполняется обновление строк, не гарантирован.  
  
## <a name="result-sets"></a>Результирующие наборы

 В зависимости от того, указали ли вы какие-либо параметры для таблицы, содержащей столбец идентификаторов, инструкция DBCC CHECKIDENT возвращает следующее сообщение для всех операций за исключением одной. Эта операция указывает новое начальное значение.  
  
`Checking identity information: current identity value '\<current identity value>', current column value '\<current column value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
 При использовании инструкции DBCC CHECKIDENT для указания нового начального значения с помощью RESEED *new_reseed_value* возвращается следующее сообщение.  
  
`Checking identity information: current identity value '\<current identity value>'. DBCC execution completed. If DBCC printed error messages, contact your system administrator.`
  
## <a name="permissions"></a>Разрешения

 Участник должен быть владельцем схемы, содержащей таблицу, либо участником предопределенной роли сервера **sysadmin**, предопределенной роли базы данных **db_owner** или предопределенной роли базы данных **db_ddladmin**.

[!INCLUDE[ssSDW](../../includes/sssdwfull-md.md)] требует разрешения **db_owner**.
  
## <a name="examples"></a>Примеры  
  
### <a name="a-resetting-the-current-identity-value-if-its-needed"></a>A. Сброс текущего значения идентификатора при необходимости  
 В следующем примере сбрасывается текущее значение идентификатора (при необходимости) для указанной таблицы в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```sql
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType');  
GO  
```  
  
### <a name="b-reporting-the-current-identity-value"></a>Б. Выдача текущего значения идентификатора

 В следующем примере возвращается текущее значение идентификатора из указанной таблицы базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]. Если значение идентификатора окажется неверным, оно не исправляется.  
  
```sql
USE AdventureWorks2012;
GO  
DBCC CHECKIDENT ('Person.AddressType', NORESEED);
GO  
```  
  
### <a name="c-forcing-the-current-identity-value-to-a-new-value"></a>В. Принудительная установка нового значения текущему значению идентификатора  
 Следующий пример принудительно устанавливает для идентификатора значение 10 в столбце `AddressTypeID` для таблицы `AddressType`. Так как в таблице уже есть строки, в следующей вставляемой строке будет использоваться значение 11, то есть новое текущее значение идентификатора, определенное для столбца, плюс 1 (шаг приращения столбца).  

```sql
USE AdventureWorks2012;  
GO  
DBCC CHECKIDENT ('Person.AddressType', RESEED, 10);  
GO  
```

### <a name="d-resetting-the-identity-value-on-an-empty-table"></a>Г. Сброс значения идентификатора в пустой таблице

 Следующий пример принудительно задает текущее значение 1 для идентификатора в столбце `ErrorLogID` таблицы `ErrorLog` после удаления всех записей из таблицы. Так как в таблице нет существующих строк, следующая вставляемая строка будет использовать в качестве значения 1, то есть новое текущее значение идентификатора, не добавляя приращение, заданное для столбца.  
  
```sql
USE AdventureWorks2012;  
GO  
TRUNCATE TABLE dbo.ErrorLog
GO
DBCC CHECKIDENT ('dbo.ErrorLog', RESEED, 1);  
GO  
```  
  
## <a name="see-also"></a>См. также:

[ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
[CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)  
[DBCC (Transact-SQL)](../../t-sql/database-console-commands/dbcc-transact-sql.md)  
[Свойство IDENTITY (Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
[Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)  
[USE (Transact-SQL)](../../t-sql/language-elements/use-transact-sql.md)  
[IDENT_SEED &#40;Transact-SQL&#41;](../../t-sql/functions/ident-seed-transact-sql.md)  
[IDENT_INCR &#40;Transact-SQL&#41;](../../t-sql/functions/ident-incr-transact-sql.md)  

---
title: sp_helptext (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helptext
- sp_helptext_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helptext
ms.assetid: 24135456-05f0-427c-884b-93cf38dd47a8
author: CarlRabeler
ms.author: carlrab
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 39bc13882e3293bca022f52240f18de696f3b7c1
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82826679"
---
# <a name="sp_helptext-transact-sql"></a>sp_helptext (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Отображает определение определенного пользователем правила, по умолчанию нешифрованной хранимой процедуры на языке [!INCLUDE[tsql](../../includes/tsql-md.md)], определенной пользователем функции на языке [!INCLUDE[tsql](../../includes/tsql-md.md)], триггера, вычисляемого столбца, ограничения CHECK, вида или системного объекта, такого как системная хранимая процедура.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helptext [ @objname = ] 'name' [ , [ @columnname = ] computed_column_name ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @objname = ] 'name'`Полное или неполное имя определяемого пользователем объекта в области схемы. Кавычки требуются, только если определяется уточненный объект. Если предоставлено полное имя таблицы, включая имя базы данных, в качестве последнего должно использоваться имя текущей базы данных. Объект должен находиться в текущей базе данных. *Name* имеет тип **nvarchar (776)** и не имеет значения по умолчанию.  
  
`[ @columnname = ] 'computed_column_name'`Имя вычисляемого столбца, для которого отображаются сведения об определении. Таблица, содержащая столбец, должна быть указана в качестве *имени*. Аргумент *column_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**Текст**|**nvarchar(255)**|Определение объекта|  
  
## <a name="remarks"></a>Примечания  
 Процедура sp_helptext отображает определение, которое используется для создания объекта во множестве строк. Каждая строка содержит 255 символов определения на языке [!INCLUDE[tsql](../../includes/tsql-md.md)]. Определение находится в столбце **определения** в представлении каталога [sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**. Определения системных объектов видимы для всех. Определения пользовательских объектов видимы владельцу объекта или участникам, которым предоставлены следующие разрешения: ALTER, CONTROL, TAKE OWNERSHIP или VIEW DEFINITION.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-displaying-the-definition-of-a-trigger"></a>A. Отображение определения триггера  
 В следующем примере показано определение триггера `dEmployee` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptext 'HumanResources.dEmployee';  
GO  
```  
  
### <a name="b-displaying-the-definition-of-a-computed-column"></a>Б. Отображение определения вычисляемого столбца  
 Следующий пример отображает определение вычисляемого столбца `TotalDue` таблицы `SalesOrderHeader` в базе данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].  
  
```  
USE AdventureWorks2012;  
GO  
sp_helptext @objname = N'AdventureWorks2012.Sales.SalesOrderHeader', @columnname = TotalDue ;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `Text`  
  
 `---------------------------------------------------------------------`  
  
 `(isnull(([SubTotal]+[TaxAmt])+[Freight],(0)))`  
  
## <a name="see-also"></a>См. также  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [sp_help (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sys.sql_modules (Transact-SQL)](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

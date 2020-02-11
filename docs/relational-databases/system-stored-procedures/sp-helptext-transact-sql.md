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
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 160d52c8c145828f6a63c104aecb17e04867cee8
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68048295"
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
 0 (успех) или 1 (сбой).  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**текст**|**nvarchar(255)**|Определение объекта|  
  
## <a name="remarks"></a>Remarks  
 Процедура sp_helptext отображает определение, которое используется для создания объекта во множестве строк. Каждая строка содержит 255 символов определения на языке [!INCLUDE[tsql](../../includes/tsql-md.md)]. Определение находится в столбце **определения** в представлении каталога [sys. sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md) .  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли **Public** . Определения системных объектов видимы для всех. Определения пользовательских объектов видимы владельцу объекта или участникам, которым предоставлены следующие разрешения: ALTER, CONTROL, TAKE OWNERSHIP или VIEW DEFINITION.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sys. sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

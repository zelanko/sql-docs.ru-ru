---
title: sp_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 10/17/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_columns_TSQL
- sp_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sp_columns
ms.assetid: 2dec79cf-2baf-4c0f-8cbb-afb1a8654e1e
caps.latest.revision: 45
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 014e40b2e47ce50765febbb05445414c21d80fba
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/27/2018
ms.locfileid: "43074180"
---
# <a name="spcolumns-transact-sql"></a>sp_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о столбце для указанных объектов, которые могут быть запрошены в текущей среде.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_columns [ @table_name = ] object  
     [ , [ @table_owner = ] owner ]   
     [ , [ @table_qualifier = ] qualifier ]   
     [ , [ @column_name = ] column ]   
     [ , [ @ODBCVer = ] ODBCVer ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@table_name=**] *объекта*  
 Имя владельца таблицы или представления, используемых для возврата сведений о каталоге. *Объект* может быть таблицы, представления или другим объектом, имеющим столбцов, таких как возвращающие табличные значения функции. *Объект* — **nvarchar(384)**, не имеет значения по умолчанию. Поиск совпадений по шаблону поддерживается.  
  
 [  **@table_owner*** =**] *владельца*  
 Имя владельца таблицы или представления, используемых для возврата сведений о каталоге. *владелец* — **nvarchar(384)**, значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается. Если *владельца* не задан, применяются правила видимости объекта по умолчанию базовой СУБД.  
  
 Если текущий пользователь является владельцем объекта с указанным именем, то возвращаются столбцы этого объекта. Если *владельца* не задан и текущий пользователь не является владельцем объекта с указанным *объект*, **sp_columns** ищет объект с указанным  *Объект* принадлежат владельцу базы данных. Если таковой существует, возвращаются столбцы этого объекта.  
  
 [  **@table_qualifier*** =**] *квалификатор*  
 Имя квалификатора объекта. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена для объектов (*квалификатор ***.*** владелец ***.*** имя*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот столбец представляет имя базы данных. В некоторых продуктах он представляет имя сервера в среде базы данных объекта.  
  
 [  **@column_name=**] *столбца*  
 Является отдельным столбцом и используется в том случае, когда нужен только один столбец информации каталога. *столбец* — **nvarchar(384)**, значение по умолчанию NULL. Если *столбец* является не указан, возвращаются все столбцы. В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], *столбец* представляет имя столбца, как указано в **syscolumns** таблицы. Поиск совпадений по шаблону поддерживается. Для максимальной совместимости клиент шлюза должен использовать только стандартное согласование SQL-92 (символы-шаблоны % и _).  
  
 [  **@ODBCVer=**] *Аргумент ODBCVer*  
 Версия используемого протокола ODBC. *Аргумент ODBCVer* — **int**, значение по умолчанию 2. Это значение соответствует ODBC версии 2. Допустимы значения 2 или 3. Различия в поведении между версиями 2 и 3, см. в разделе ODBC **SQLColumns** спецификации.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
 **Sp_columns** хранимая процедура каталога эквивалентно **SQLColumns** в ODBC. Возвращенные результаты сортируются по **TABLE_QUALIFIER**, **TABLE_OWNER**, и **TABLE_NAME**.  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|Имя квалификатора объекта. Это поле может иметь значение NULL.|  
|**TABLE_OWNER**|**sysname**|Имя владельца объекта. Это поле всегда возвращает значение.|  
|**ИМЯ_ТАБЛИЦЫ**|**sysname**|Имя объекта. Это поле всегда возвращает значение.|  
|**COLUMN_NAME**|**sysname**|Имя столбца для каждого столбца **TABLE_NAME** возвращается. Это поле всегда возвращает значение.|  
|**DATA_TYPE**|**smallint**|Целочисленный код типа данных ODBC. Если этот тип данных не может быть сопоставлен с типом данных ODBC, возвращается значение NULL. Имя типа данных в собственном формате возвращается в **TYPE_NAME** столбца.|  
|**TYPE_NAME**|**sysname**|Тип данных в символьном представлении. Название типа предоставляется базовой СУБД.|  
|**PRECISION**|**int**|Количество значащих цифр. Возвращаемое значение для **точности** основано на десятичной системе счисления.|  
|**LENGTH**|**int**|Перенос объема данных. <sup>1</sup>|  
|**МАСШТАБ**|**smallint**|Число цифр справа от десятичной запятой.|  
|**ОСНОВАНИЕ СИСТЕМЫ СЧИСЛЕНИЯ**|**smallint**|Основание системы счисления числовых типов данных.|  
|**ДОПУСКАЮЩИЙ ЗНАЧЕНИЕ NULL**|**smallint**|Указывает возможность содержать значение NULL.<br /><br /> 1 = значение NULL допустимо.<br /><br /> 0 = значение NULL недопустимо.|  
|**"ПРИМЕЧАНИЯ"**|**varchar(254)**|Это поле всегда возвращает значение NULL.|  
|**COLUMN_DEF**|**nvarchar(4000)**|Значение столбца по умолчанию.|  
|**SQL_DATA_TYPE**|**smallint**|Значение типа данных SQL в том же виде, что и в поле TYPE дескриптора. Этот столбец совпадает со значением **DATA_TYPE** столбца, за исключением **datetime** и SQL-92 **интервал** типов данных. Этот столбец всегда возвращает значение.|  
|**SQL_DATETIME_SUB**|**smallint**|Код подтипа для **datetime** и SQL-92 **интервал** типов данных. Для других типов данных этот столбец возвращает значение NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Максимальная длина столбца символьного или целочисленного типа в байтах. Для всех других типов данных этот столбец возвращает значение NULL.|  
|**ORDINAL_POSITION**|**int**|Порядковый номер столбца в объекте. Первый столбец в объекте имеет порядковый номер 1. Этот столбец всегда возвращает значение.|  
|**IS_NULLABLE**|**varchar(254)**|Допустимость значений NULL для столбца объекта. Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO SQL, не может вернуть пустую строку.<br /><br /> YES = Столбец может содержать значение NULL.<br /><br /> NO = Столбец не может содержать значения NULL.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Возвращаемое значение для этого столбца отличается от значения, возвращаемого в **NULLABLE** столбца.|  
|**SS_DATA_TYPE**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных используется для расширенных хранимых процедур. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
  
 <sup>1</sup> Дополнительные сведения см. в документации по Microsoft ODBC.  
  
## <a name="permissions"></a>Разрешения  
 Требует разрешения SELECT и VIEW DEFINITION на схему.  
  
## <a name="remarks"></a>Примечания  
 **sp_columns** соответствует требованиям к идентификаторам с разделителями. Дополнительные сведения см. в разделе [Идентификаторы баз данных](../../relational-databases/databases/database-identifiers.md).  
  
## <a name="examples"></a>Примеры  
 Следующий пример возвращает данные столбца для указанной таблицы.  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_columns @table_name = N'Department',  
   @table_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 Следующий пример возвращает данные столбца для указанной таблицы.  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_columns @table_name = N'DimEmployee',  
   @table_owner = N'dbo';  
```  
  
## <a name="see-also"></a>См. также  
 [sp_tables &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-tables-transact-sql.md)   
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  



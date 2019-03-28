---
title: sp_sproc_columns (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_sproc_columns
- sp_sproc_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_sproc_columns
ms.assetid: 62c18c21-35c5-4772-be0d-ffdcc19c97ab
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8fd3e7ba4880a5d908991d32faaa9c1a5275976f
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58533996"
---
# <a name="spsproccolumns-transact-sql"></a>sp_sproc_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  Возвращает сведения о столбце для одной хранимой процедуры или определяемой пользователем функции в текущем окружении.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_sproc_columns [[@procedure_name = ] 'name']   
    [ , [@procedure_owner = ] 'owner']   
    [ , [@procedure_qualifier = ] 'qualifier']   
    [ , [@column_name = ] 'column_name']  
    [ , [@ODBCVer = ] 'ODBCVer']  
    [ , [@fUsePattern = ] 'fUsePattern']  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @procedure_name = ] 'name'` — Имя процедуры, используемой для возврата сведений о каталоге. *имя* — **nvarchar (** 390 **)**, значение по умолчанию %, означающее все таблицы в текущей базе данных. Поиск совпадений по шаблону поддерживается.  
  
`[ @procedure_owner = ] 'owner'` — Это имя владельца процедуры. *владелец*— **nvarchar (** 384 **)**, значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается. Если *владельца* не задан, применяются правила видимости процедуры по умолчанию базовой СУБД.  
  
 Если текущий пользователь является владельцем процедуры с указанным именем, возвращаются сведения о процедуре. Если *владельца*не задан и текущий пользователь не является владельцем процедуры с указанным именем, **sp_sproc_columns** ищет процедуру с указанным именем, принадлежащий владельцу базы данных. Если процедура существует, возвращаются сведения о ее столбцах.  
  
`[ @procedure_qualifier = ] 'qualifier'` — Имя квалификатора процедуры. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*qualifier.owner.name*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот аргумент представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
`[ @column_name = ] 'column_name'` Состоит из единственного столбца и используется только один столбец информации каталога при необходимости. *column_name* — **nvarchar (** 384 **)**, значение по умолчанию NULL. Если *column_name* — этот параметр опущен, возвращаются все столбцы. Поиск совпадений по шаблону поддерживается. Для максимальной совместимости клиент шлюза должен использовать только согласование установленного образца ISO (символы-шаблоны % и _).  
  
`[ @ODBCVer = ] 'ODBCVer'` Используется ли используемая версия ODBC. *Аргумент ODBCVer* — **int**, значение по умолчанию 2, означающее ODBC версии 2.0. Дополнительные сведения о различиях между ODBC версии 2.0 и ODBC версии 3.0 см. ODBC **SQLProcedureColumns** спецификации для ODBC версии 3.0  
  
`[ @fUsePattern = ] 'fUsePattern'` Определяет, следует ли рассматривать символы подчеркивания (_), процента (%) и символы скобок ([]). Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *Шаблонов* — **бит**, значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|Имя квалификатора процедуры. Этот столбец может принимать значение NULL.|  
|**PROCEDURE_OWNER**|**sysname**|Имя владельца процедуры. Этот столбец всегда возвращает значение.|  
|**PROCEDURE_NAME**|**nvarchar(** 134 **)**|Имя процедуры. Этот столбец всегда возвращает значение.|  
|**COLUMN_NAME**|**sysname**|Имя столбца для каждого столбца **TABLE_NAME** возвращается. Этот столбец всегда возвращает значение.|  
|**COLUMN_TYPE**|**smallint**|Это поле всегда возвращает значение:<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE|  
|**DATA_TYPE**|**smallint**|Целочисленный код для типа данных ODBC. Если этот тип данных нельзя сопоставить с типом ISO, то значением будет NULL. Имя типа данных в собственном формате возвращается в **TYPE_NAME** столбца.|  
|**TYPE_NAME**|**sysname**|Строковое представление типа данных. Это имя типа данных, как представлено соответствующей СУБД.|  
|**PRECISION**|**int**|Количество значащих цифр. Возвращаемое значение для **точности** основано на десятичной системе счисления.|  
|**LENGTH**|**int**|Размер передаваемых данных.|  
|**МАСШТАБ**|**smallint**|Число цифр справа от десятичной запятой.|  
|**RADIX**|**smallint**|Основание системы счисления для числовых типов.|  
|**ДОПУСКАЮЩИЙ ЗНАЧЕНИЕ NULL**|**smallint**|Определяет допустимость значений NULL:<br /><br /> 1 = Может быть создан тип данных, допускающий значения NULL.<br /><br /> 0 = значения NULL недопустимы.|  
|**"ПРИМЕЧАНИЯ"**|**varchar(** 254 **)**|Описание столбца процедуры. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
|**COLUMN_DEF**|**nvarchar(** 4000 **)**|Значение столбца по умолчанию.|  
|**SQL_DATA_TYPE**|**smallint**|Значение типа данных SQL, как оно отображается в **тип** поле дескриптора. Этот столбец содержит то же значение, что и столбец **DATA_TYPE**, за исключением типов данных **datetime** и ISO **interval**. Этот столбец всегда возвращает значение.|  
|**SQL_DATETIME_SUB**|**smallint**|Дополнительный код **datetime** ISO **interval**, если значение **SQL_DATA_TYPE** равно **SQL_DATETIME** или **SQL_INTERVAL**. Для типов данных, отличных от **datetime** и ISO **интервал**, это поле имеет значение NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Максимальная длина в байтах **символ** или **двоичных** столбце с типом данных. Для всех других типов данных этот столбец возвращает значение NULL.|  
|**ORDINAL_POSITION**|**int**|Порядковый номер столбца в таблице. Первый столбец в таблице имеет порядковый номер 1. Этот столбец всегда возвращает значение.|  
|**IS_NULLABLE**|**varchar(254)**|Способность столбца таблицы содержать значение NULL. Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO, не может возвращать пустую строку.<br /><br /> Отображает YES, если столбец может включать значения NULL, и NO, если столбец не может содержать значения NULL.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Значение, возвращаемое в данном столбце, отличается от значения, возвращаемого в столбце NULLABLE.|  
|**SS_DATA_TYPE**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных используется для расширенных хранимых процедур. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
  
## <a name="remarks"></a>Примечания  
 **sp_sproc_columns** эквивалентен **SQLProcedureColumns** в ODBC. Возвращенные результаты сортируются по **PROCEDURE_QUALIFIER**, **PROCEDURE_OWNER**, **PROCEDURE_NAME**и порядок, в котором параметры появляются в процедуре Определение.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры каталога &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

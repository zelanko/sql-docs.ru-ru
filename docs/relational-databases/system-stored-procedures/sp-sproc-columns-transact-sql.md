---
title: "sp_sproc_columns (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_sproc_columns
- sp_sproc_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_sproc_columns
ms.assetid: 62c18c21-35c5-4772-be0d-ffdcc19c97ab
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9488e94ffa0d3532ce72e421f5deadaf1acbed77
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
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
 [  **@procedure_name =** ] **"***имя***"**  
 Название процедуры, используемой для возврата сведений о каталоге. *имя* — **nvarchar (**390**)**, по умолчанию %, означающее все таблицы в текущей базе данных. Поиск совпадений по шаблону поддерживается.  
  
 [  **@procedure_owner =**] **"***владельца***"**  
 Имя владельца процедуры. *владелец*— **nvarchar (**384**)**, значение по умолчанию NULL. Поиск совпадений по шаблону поддерживается. Если *владельца* не указан, применяются правила видимости процедуры по умолчанию базовой СУБД.  
  
 Если текущий пользователь является владельцем процедуры с указанным именем, возвращаются сведения о процедуре. Если *владельца*не указан и текущий пользователь не является владельцем процедуры с указанным именем, **sp_sproc_columns** ищет процедуру с указанным именем, владельцем которой является владелец базы данных. Если процедура существует, возвращаются сведения о ее столбцах.  
  
 [  **@procedure_qualifier =**] **"***квалификатор***"**  
 Имя квалификатора процедуры. *квалификатор* — **sysname**, значение по умолчанию NULL. Различные продукты СУБД поддерживают трехкомпонентные имена таблиц (*qualifier.owner.name*). В [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] этот аргумент представляет имя базы данных. В некоторых СУБД он представляет имя сервера в среде базы данных, где находится таблица.  
  
 [  **@column_name =**] **"***column_name***"**  
 Одиночный столбец, используемый, если нужен только один столбец информации каталога. *column_name* — **nvarchar (**384**)**, значение по умолчанию NULL. Если *column_name* будет указан, возвращаются все столбцы. Поиск совпадений по шаблону поддерживается. Для максимальной совместимости клиент шлюза должен использовать только согласование установленного образца ISO (символы-шаблоны % и _).  
  
 [  **@ODBCVer =**] **"***Аргумент ODBCVer***"**  
 Версия используемого протокола ODBC. *Аргумент ODBCVer* — **int**, значение по умолчанию 2, означающее ODBC версии 2.0. Дополнительные сведения о различиях между ODBC 2.0 и ODBC версии 3.0 см. ODBC **SQLProcedureColumns** спецификации ODBC версии 3.0  
  
 [  **@fUsePattern =**] **"***шаблонов***"**  
 Определяет, следует ли рассматривать подчеркивание (_), процент (%) и скобку ([ ]) как символы-шаблоны. Допустимые значения: 0 (сопоставление с шаблоном отключено) и 1 (сопоставление с шаблоном включено). *Шаблонов* — **бит**, значение по умолчанию 1.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 Нет  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|Имя квалификатора процедуры. Этот столбец может принимать значение NULL.|  
|**PROCEDURE_OWNER**|**sysname**|Имя владельца процедуры. Этот столбец всегда возвращает значение.|  
|**PROCEDURE_NAME**|**nvarchar (**134**)**|Имя процедуры. Этот столбец всегда возвращает значение.|  
|**COLUMN_NAME**|**sysname**|Имя столбца для каждого столбца таблицы **TABLE_NAME** возвращается. Этот столбец всегда возвращает значение.|  
|**COLUMN_TYPE**|**smallint**|Это поле всегда возвращает значение:<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE|  
|**ТИП ДАННЫХ**|**smallint**|Целочисленный код для типа данных ODBC. Если этот тип данных нельзя сопоставить с типом ISO, то значением будет NULL. Собственное имя типа данных возвращается в **TYPE_NAME** столбца.|  
|**TYPE_NAME**|**sysname**|Строковое представление типа данных. Это имя типа данных, как представлено соответствующей СУБД.|  
|**ТОЧНОСТЬ**|**int**|Количество значащих цифр. Возвращаемое значение для **точности** столбец имеет десятичную форму.|  
|**LENGTH**|**int**|Размер передаваемых данных.|  
|**МАСШТАБ**|**smallint**|Число цифр справа от десятичной запятой.|  
|**ОСНОВАНИЕ СИСТЕМЫ СЧИСЛЕНИЯ**|**smallint**|Основание системы счисления для числовых типов.|  
|**ДОПУСКАЮЩИЕ ЗНАЧЕНИЯ NULL**|**smallint**|Определяет допустимость значений NULL:<br /><br /> 1 = Может быть создан тип данных, допускающий значения NULL.<br /><br /> 0 = значения NULL недопустимы.|  
|**ПРИМЕЧАНИЯ**|**varchar (**254**)**|Описание столбца процедуры. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не возвращает значение для этого столбца.|  
|**COLUMN_DEF**|**nvarchar (**4000**)**|Значение столбца по умолчанию.|  
|**SQL_DATA_TYPE**|**smallint**|Значение типа данных SQL, как оно отображается в **тип** дескриптора. Этот столбец содержит то же, как **DATA_TYPE** столбца, за исключением **datetime** и ISO **интервал** типов данных. Этот столбец всегда возвращает значение.|  
|**SQL_DATETIME_SUB**|**smallint**|**Datetime** ISO **интервал** Доп. Если значение **SQL_DATA_TYPE** — **SQL_DATETIME** или **SQL_INTERVAL**. Для типов данных, отличный от **datetime** и ISO **интервал**, это поле имеет значение NULL.|  
|**CHAR_OCTET_LENGTH**|**int**|Максимальная длина в байтах **символ** или **двоичных** столбец типа данных. Для всех других типов данных этот столбец возвращает значение NULL.|  
|**ORDINAL_POSITION**|**int**|Порядковый номер столбца в таблице. Первый столбец в таблице имеет порядковый номер 1. Этот столбец всегда возвращает значение.|  
|**IS_NULLABLE**|**varchar(254)**|Способность столбца таблицы содержать значение NULL. Допустимость значений NULL определяется в соответствии с правилами ISO. СУБД, совместимая с ISO, не может возвращать пустую строку.<br /><br /> Отображает YES, если столбец может включать значения NULL, и NO, если столбец не может содержать значения NULL.<br /><br /> Если допустимость значения NULL неизвестна, то этот столбец возвращает строку нулевой длины.<br /><br /> Значение, возвращаемое в данном столбце, отличается от значения, возвращаемого в столбце NULLABLE.|  
|**SS_DATA_TYPE**|**tinyint**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных используется для расширенных хранимых процедур. Дополнительные сведения см. в разделе [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md).|  
  
## <a name="remarks"></a>Замечания  
 **sp_sproc_columns** эквивалентно **SQLProcedureColumns** в ODBC. Возвращенные результаты сортируются по **PROCEDURE_QUALIFIER**, **PROCEDURE_OWNER**, **имя_процедуры**и порядок, в котором параметры появляются в процедуре Определение.  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение SELECT для схемы.  
  
## <a name="see-also"></a>См. также:  
 [Каталога хранимых процедур &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

---
title: sp_datatype_info_90 (хранилище данных SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/13/2017
ms.prod: ''
ms.prod_service: sql-data-warehouse, pdw
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1d043964-dc6e-4c3e-ab61-bc444d5e25ae
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: fd24c36801d4b17217ebe688d51913618697d6a5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47830243"
---
# <a name="spdatatypeinfo90-sql-data-warehouse"></a>sp_datatype_info_90 (хранилище данных SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  Возвращает сведения о типах данных, поддерживаемых текущей средой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
sp_datatype_info_90 [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@data_type=** ] *data_type*  
 Кодовый номер типа данных. Для получения списка всех типов данных пропустите этот аргумент. *data_type* — **int**, значение по умолчанию 0.  
  
 [  **@ODBCVer=** ] *odbc_version*  
 Версия используемого протокола ODBC. *odbc_version* — **tinyint**, значение по умолчанию 2.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**sysname**|Тип данных, зависящий от СУБД.|  
|DATA_TYPE|**smallint**|Код типа ODBC, с которым сопоставляются все столбцы данного типа.|  
|PRECISION|**int**|Максимальная точность типа данных в источнике данных. Для типов данных, к которым понятие точности не применимо, возвращается значение NULL. Значение, возвращаемое для столбца PRECISION, имеет десятичную форму.|  
|LITERAL_PREFIX|**varchar (** 32 **)**|Символ или символы, используемые перед константой. Например, одинарная кавычка (**"**) для символьных типов и 0 x для двоичного файла.|  
|LITERAL_SUFFIX|**varchar (** 32 **)**|Символ или символы, используемые после константы. Например, одинарная кавычка (**"**) для символьных типов и кавычки для двоичного файла.|  
|CREATE_PARAMS|**varchar (** 32 **)**|Описание параметров создания типа данных. Например **десятичное** является «точность, масштаб», **float** имеет значение NULL, и **varchar** — «max_length».|  
|NULLABLE|**smallint**|Указывает возможность содержать значение NULL.<br /><br /> 1 = значения NULL допускаются.<br /><br /> 0 = значения NULL не допускаются.|  
|CASE_SENSITIVE|**smallint**|Чувствительность к регистру.<br /><br /> 1 = все столбцы этого типа чувствительны к регистру (для параметров сортировки).<br /><br /> 0 = все столбцы этого типа не чувствительны к регистру.|  
|SEARCHABLE|**smallint**|Задает возможность поиска для типа столбца:<br /><br /> 1 = поиск невозможен;<br /><br /> 2 = возможен поиск с оператором LIKE;<br /><br /> 3 = возможен поиск с предложением WHERE;<br /><br /> 4 = возможен поиск с предложением WHERE или оператором LIKE.|  
|UNSIGNED_ATTRIBUTE|**smallint**|Знак типа данных.<br /><br /> 1 = тип данных без знака.<br /><br /> 0 = тип данных со знаком.|  
|MONEY|**smallint**|Указывает **деньги** тип данных.<br /><br /> 1 = **деньги** тип данных.<br /><br /> 0 = не **деньги** тип данных.|  
|AUTO_INCREMENT|**smallint**|Автоматическое приращение.<br /><br /> 1 = автоматическое приращение выполняется.<br /><br /> 0 = автоматическое приращение не выполняется.<br /><br /> NULL = атрибут неприменим.<br /><br /> Приложение может вставлять значение в столбец с этим атрибутом, но не может обновлять значения такого столбца. За исключением элемента **бит** тип данных, параметр AUTO_INCREMENT допустим только для типов данных, входящих в точных или приблизительных числовых категории типов данных.|  
|LOCAL_TYPE_NAME|**sysname**|Локализованная версия имени типа данных, которое зависит от источника данных. Например, тип DECIMAL называется по-французски DECIMALE. Если локализованное имя не поддерживается источником данных, возвращается значение NULL.|  
|MINIMUM_SCALE|**smallint**|Минимальный масштаб типа данных в источнике данных. Если тип данных имеет фиксированный масштаб, это значение содержится и в столбце MINIMUM_SCALE, и в столбце MAXIMUM_SCALE. Для типов данных, к которым понятие масштаба не применимо, возвращается значение NULL.|  
|MAXIMUM_SCALE|**smallint**|Максимальный масштаб типа данных в источнике данных. Если максимальный масштаб не определен отдельно в источнике данных и равен максимальной точности, этот столбец содержит то же значение, что и столбец PRECISION.|  
|SQL_DATA_TYPE|**smallint**|Значение типа данных SQL в том же виде, что и в поле TYPE дескриптора. Этот столбец является таким же, как столбец DATA_TYPE, за исключением **datetime** и ANSI **интервал** типов данных. Это поле всегда возвращает значение.|  
|SQL_DATETIME_SUB|**smallint**|**DateTime** или ANSI **интервал** Доп. Если значение SQL_DATA_TYPE равно SQL_DATETIME или SQL_INTERVAL. Для типов данных, отличных от **datetime** и ANSI **интервал**, это поле имеет значение NULL.|  
|NUM_PREC_RADIX|**int**|Количество битов или разрядов, используемое при вычислении максимального числа, которое может содержаться в столбце. Если тип данных является приблизительным числовым типом, этот столбец содержит значение 2, которое говорит о том, что тип включает несколько битов. Если тип данных является точным числовым типом, этот столбец содержит значение 10, которое говорит о том, что тип включает несколько десятичных разрядов. В противном случае этот столбец содержит значение NULL. Объединив точность с основанием системы счисления, приложение может определить максимальное число, которое может содержаться в столбце.|  
|INTERVAL_PRECISION|**smallint**|Значение точности интервала Если *data_type* — **интервал**; в противном случае — NULL.|  
|USERTYPE|**smallint**|**usertype** значение из таблицы systypes.|  
  
## <a name="remarks"></a>Примечания  
 sp_datatype_info эквивалентна SQLGetTypeInfo в ODBC. Возвращаемые этой процедурой результаты упорядочиваются по значению DATA_TYPE, а затем по степени соответствия типа данных аналогичному типу данных ODBC SQL.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>Примеры: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] и [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 В следующем примере извлекаются сведения о **sysname** и **nvarchar** типы данных, указав *data_type* значение `-9`.  
  
```  
USE master;  
GO  
EXEC sp_datatype_info_90 -9;  
GO  
```  
  
## <a name="see-also"></a>См. также  
 [Хранимые процедуры хранилища данных SQL](../../relational-databases/system-stored-procedures/sql-data-warehouse-stored-procedures.md)   
 [Типы данных (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)  
  
  


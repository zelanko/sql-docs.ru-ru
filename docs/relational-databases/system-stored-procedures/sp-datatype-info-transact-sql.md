---
title: sp_datatype_info (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 05/25/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_datatype_info_TSQL
- sp_datatype_info
dev_langs:
- TSQL
helpviewer_keywords:
- sp_datatype_info
ms.assetid: 045f3b5d-6bb7-4748-8b4c-8deb4bc44147
author: stevestein
ms.author: sstein
ms.openlocfilehash: 39e8f688c23cffb1512be1cd1142d38c010668a7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68108303"
---
# <a name="sp_datatype_info-transact-sql"></a>Хранимая процедура sp_datatype_info (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  Возвращает сведения о типах данных, поддерживаемых текущей средой.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_datatype_info [ [ @data_type = ] data_type ]   
     [ , [ @ODBCVer = ] odbc_version ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @data_type = ] data_type`Номер кода для указанного типа данных. Для получения списка всех типов данных пропустите этот аргумент. *data_type* имеет **тип int**и значение по умолчанию 0.  
  
`[ @ODBCVer = ] odbc_version`Используемая версия ODBC. *odbc_version* имеет тип **tinyint**и значение по умолчанию 2.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 None  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|TYPE_NAME|**имеет sysname**|Тип данных, зависящий от СУБД.|  
|DATA_TYPE|**smallint**|Код типа ODBC, с которым сопоставляются все столбцы данного типа.|  
|PRECISION|**int**|Максимальная точность типа данных в источнике данных. Для типов данных, к которым понятие точности не применимо, возвращается значение NULL. Значение, возвращаемое для столбца PRECISION, имеет десятичную форму.|  
|LITERAL_PREFIX|**varchar (** 32 **)**|Символ или символы, используемые перед константой. Например, одинарная кавычка (**'**) для символьных типов и 0x для binary.|  
|LITERAL_SUFFIX|**varchar (** 32 **)**|Символ или символы, используемые после константы. Например, одинарная кавычка (**'**) для символьных типов и без кавычек для binary.|  
|CREATE_PARAMS|**varchar (** 32 **)**|Описание параметров создания типа данных. Например, **десятичный** тип "точность, масштаб", **float** имеет значение null, а **varchar** — "max_length".|  
|NULLABLE|**smallint**|Указывает возможность содержать значение NULL.<br /><br /> 1 = значения NULL допускаются.<br /><br /> 0 = значения NULL не допускаются.|  
|CASE_SENSITIVE|**smallint**|Чувствительность к регистру.<br /><br /> 1 = все столбцы этого типа чувствительны к регистру (для параметров сортировки).<br /><br /> 0 = все столбцы этого типа не чувствительны к регистру.|  
|SEARCHABLE|**smallint**|Задает возможность поиска для типа столбца:<br /><br /> 1 = поиск невозможен;<br /><br /> 2 = возможен поиск с оператором LIKE;<br /><br /> 3 = возможен поиск с предложением WHERE;<br /><br /> 4 = возможен поиск с предложением WHERE или оператором LIKE.|  
|UNSIGNED_ATTRIBUTE|**smallint**|Знак типа данных.<br /><br /> 1 = тип данных без знака.<br /><br /> 0 = тип данных со знаком.|  
|MONEY|**smallint**|Указывает тип данных **money** .<br /><br /> 1 = тип данных **money** .<br /><br /> 0 = не тип данных **money** .|  
|AUTO_INCREMENT|**smallint**|Автоматическое приращение.<br /><br /> 1 = автоматическое приращение выполняется.<br /><br /> 0 = автоматическое приращение не выполняется.<br /><br /> NULL = атрибут неприменим.<br /><br /> Приложение может вставлять значение в столбец с этим атрибутом, но не может обновлять значения такого столбца. За исключением типа данных **bit** , AUTO_INCREMENT допустимы только для типов данных, относящихся к категориям точных числовых и приблизительных числовых типов данных.|  
|LOCAL_TYPE_NAME|**имеет sysname**|Локализованная версия имени типа данных, которое зависит от источника данных. Например, тип DECIMAL называется по-французски DECIMALE. Если локализованное имя не поддерживается источником данных, возвращается значение NULL.|  
|MINIMUM_SCALE|**smallint**|Минимальный масштаб типа данных в источнике данных. Если тип данных имеет фиксированный масштаб, это значение содержится и в столбце MINIMUM_SCALE, и в столбце MAXIMUM_SCALE. Для типов данных, к которым понятие масштаба не применимо, возвращается значение NULL.|  
|MAXIMUM_SCALE|**smallint**|Максимальный масштаб типа данных в источнике данных. Если максимальный масштаб не определен отдельно в источнике данных и равен максимальной точности, этот столбец содержит то же значение, что и столбец PRECISION.|  
|SQL_DATA_TYPE|**smallint**|Значение типа данных SQL в том же виде, что и в поле TYPE дескриптора. Этот столбец аналогичен столбцу DATA_TYPE, за исключением типов данных **DateTime** и ANSI **Interval** . Это поле всегда возвращает значение.|  
|SQL_DATETIME_SUB|**smallint**|Если значение SQL_DATA_TYPE равно SQL_DATETIME или SQL_INTERVAL, то используется подкод **интервала** **DateTime** или ANSI. Для типов данных, отличных от **DateTime** **и ANSI,** это поле имеет значение null.|  
|NUM_PREC_RADIX|**int**|Количество битов или разрядов, используемое при вычислении максимального числа, которое может содержаться в столбце. Если тип данных является приблизительным числовым типом, этот столбец содержит значение 2, которое говорит о том, что тип включает несколько битов. Если тип данных является точным числовым типом, этот столбец содержит значение 10, которое говорит о том, что тип включает несколько десятичных разрядов. В противном случае этот столбец содержит значение NULL. Объединив точность с основанием системы счисления, приложение может определить максимальное число, которое может содержаться в столбце.|  
|INTERVAL_PRECISION|**smallint**|Значение для начальной точности интервала, если *data_type* — **интервал**; в противном случае — NULL.|  
|USERTYPE|**smallint**|значение **usertype** из таблицы systypes.|  
  
## <a name="remarks"></a>Remarks  
 sp_datatype_info эквивалентен SQLGetTypeInfo в ODBC. Возвращаемые этой процедурой результаты упорядочиваются по значению DATA_TYPE, а затем по степени соответствия типа данных аналогичному типу данных ODBC SQL.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в роли public.  
  
## <a name="examples"></a>Примеры  
 В следующем примере извлекаются сведения для типов данных **sysname** и **nvarchar** путем указания *data_type* значения `-9`.  
  
```  
USE master;  
GO  
EXEC sp_datatype_info -9;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Ядро СУБД хранимых процедур &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [Типы данных &#40;&#41;Transact-SQL](../../t-sql/data-types/data-types-transact-sql.md)   
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

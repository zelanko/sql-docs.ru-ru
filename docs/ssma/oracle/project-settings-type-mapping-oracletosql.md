---
title: Параметры (сопоставление типов) проекта (OracleToSQL) | Документы Microsoft
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: ssma-oracle
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology:
- sql-ssma
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4bb8466e-2199-4f00-8513-b04e9586723d
caps.latest.revision: 8
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.workload: Inactive
ms.openlocfilehash: 84d47276324b7616a30aff3d14949230595194c4
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="project-settings-type-mapping-oracletosql"></a>Параметры (сопоставление типов) проекта (OracleToSQL)
На странице сопоставление типов **параметры проекта** диалоговое окно содержит настройки, установленные как SSMA преобразует типы данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных.  
  
Сопоставление типов можно найти в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Для задания параметров для всех будущих проектов SSMA на **средства** меню **параметры проекта по умолчанию**, выберите тип проекта миграции, для которого требуются параметры для просмотра и изменения из **миграции целевой версии** раскрывающийся список и выберите **сопоставление типов** в нижней части левой панели.  
  
-   Чтобы указать параметры для текущего проекта на **средства** меню **параметры проекта**и нажмите кнопку **сопоставление типов** в нижней части левой панели.  
  
Чтобы указать параметры для текущего объекта или класса объектов, используйте **сопоставление типов** в окне источника SSMA.  
  
## <a name="options"></a>Параметры  
В следующей таблице показаны **сопоставление типов** параметры:  
  
**Исходный тип**  
Сопоставленный тип данных Oracle.  
  
**Тип целевого объекта**  
Целевой объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] тип данных для указанного типа данных Oracle.  
  
См. в следующем разделе для SSMA по умолчанию для сопоставления типов Oracle в таблицах.  
  
**Добавить**  
Щелкните, чтобы добавить в список сопоставления типа данных.  
  
**Правка**  
Щелкните для изменения выбранного типа данных в списке сопоставления.  
  
**Удалить**  
Щелкните, чтобы удалить сопоставление типов данных, выбранного из списка сопоставления.  
  
**По умолчанию**  
Щелкните, чтобы сбросить список сопоставления типа по умолчанию SSMA.  
  
## <a name="default-type-mappings"></a>Сопоставления типов по умолчанию  
SSMA для Oracle настраивается нестандартные сопоставления типов для аргументов, столбцы, локальные переменные и возвращаемые значения. Сопоставление по умолчанию для аргументов и возвращаемых типов почти ничем не отличается.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>По умолчанию тип аргумента и возвращает сопоставление типов значения  
Следующая таблица содержит сопоставление типов данных по умолчанию для аргументов и возвращаемых значений.  
  
|Тип данных Oracle|По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] тип данных|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|число с плавающей запятой [53]|  
|binary_float|число с плавающей запятой [53]|  
|binary_integer|int|  
|большой двоичный объект|varbinary(max)|  
|boolean|bit|  
|char;|varchar(max)|  
|char varying|varchar(max)|  
|character|varchar(max)|  
|character varying|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|Decimal|число с плавающей запятой [53]|  
|число двойной точности|число с плавающей запятой [53]|  
|float|число с плавающей запятой [53]|  
|int|int|  
|integer|int|  
|long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [\*... 8000]<sup>*</sup>|varbinary [*]|  
|Long raw [8001..\*]<sup>*</sup>|varbinary(max)|  
|Национальный char|nvarchar(max)|  
|Национальный char переменной|nvarchar(max)|  
|символов национального алфавита|nvarchar(max)|  
|изменение символов национального алфавита<sup>**</sup>|nvarchar(max)|  
|изменение символов национального алфавита<sup>*</sup>|nvarchar(max)|  
|NCHAR|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|number|число с плавающей запятой [53]|  
|numeric|число с плавающей запятой [53]|  
|NVARCHAR2|nvarchar(max)|  
|pls_integer|int|  
|raw|varbinary(max)|  
|real|число с плавающей запятой [53]|  
|RowId|uniqueidentifier|  
|Signtype|smallint|  
|smallint|smallint|  
|строка|varchar(max)|  
|TIMESTAMP|datetime2|  
|Отметка времени с местным часовым поясом|datetimeoffset|  
|Отметка времени с часовым поясом|datetimeoffset|  
|Urowid|uniqueidentifier|  
|varchar|varchar(max)|  
|VARCHAR2|varchar(max)|  
|Xmltype|xml|  
  
<sup>*</sup> Применяется для возврата значения только сопоставления типов.  
  
<sup>**</sup> Применяется к аргумента только сопоставления типов.  
  
### <a name="default-column-type-mapping"></a>Сопоставление типа столбца по умолчанию  
Следующая таблица содержит сопоставление типов по умолчанию для столбцов.  
  
|Тип данных Oracle|По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] тип данных|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|число с плавающей запятой [53]|  
|binary_float|число с плавающей запятой [53]|  
|большой двоичный объект|varbinary(max)|  
|char;|char;|  
|переменной типа char [*.. \*]|varchar [*]|  
|char [*.. \*]|char [*]|  
|character|char;|  
|символ varying [*.. \*]|varchar [*]|  
|символ [*.. \*]|char [*]|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|DEC [*.. \*]|DEC [*] [0]|  
|dec[*..\*][\*..\*]|dec[*][\*]|  
|Decimal|decimal[38][0]|  
|Decimal [*.. \*]|Decimal [*] [0]|  
|Decimal [*.. \*][\*.. \*]|Decimal [*] [\*]|  
|число двойной точности|число с плавающей запятой [53]|  
|float|число с плавающей запятой [53]|  
|число с плавающей запятой [*.. 53]|число с плавающей запятой [*]|  
|число с плавающей запятой [54.. *]|число с плавающей запятой [53]|  
|int|int|  
|integer|int|  
|long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [*.. 8000]|varbinary [*]|  
|Long raw [8001.. *]|varbinary(max)|  
|Long varchar|varchar(max)|  
|длинные [*.. 8000]|varchar [*]|  
|длинные [8001.. *]|varchar(max)|  
|Национальный char|NCHAR|  
|Национальный char переменной [*.. \*]|nvarchar [*]|  
|Национальный char [*.. \*]|nchar [*]|  
|символов национального алфавита|NCHAR|  
|изменение символов национального алфавита [*.. \*]|nvarchar [*]|  
|национальных символов [*.. \*]|nchar [*]|  
|NCHAR|NCHAR|  
|nchar [*]|nchar [*]|  
|NCLOB|nvarchar(max)|  
|number|число с плавающей запятой [53]|  
|Номер [*.. \*]|числовой [*]|  
|Номер [*.. \*][\*.. \*]|числовой [*] [\*]|  
|numeric|numeric|  
|числовые [*.. \*]|числовой [*]|  
|numeric[*..\*][\*..\*]|числовой [*] [\*]|  
|NVARCHAR2 [*.. \*]|nvarchar [*]|  
|Необработанный [*.. \*]|varbinary [*]|  
|real|число с плавающей запятой [53]|  
|RowId|uniqueidentifier|  
|smallint|smallint|  
|TIMESTAMP|datetime2|  
|Отметка времени с местным часовым поясом|datetimeoffset|  
|Отметка времени с местным часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Отметка времени с часовым поясом|datetimeoffset|  
|Отметка времени с часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Отметка времени [*.. \*]|datetime2 [*]|  
|Urowid|uniqueidentifier|  
|urowid [*.. \*]|uniqueidentifier|  
|varchar [*.. \*]|varchar [*]|  
|VARCHAR2 [*.. \*]|varchar [*]|  
|Xmltype|xml|  
  
### <a name="default-local-variable-type-mapping"></a>Сопоставление типа локальной переменной по умолчанию  
Следующая таблица содержит сопоставление типов по умолчанию для локальных переменных.  
  
|Тип данных Oracle|По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] тип данных|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|число с плавающей запятой [53]|  
|binary_float|число с плавающей запятой [53]|  
|binary_interger|int|  
|BLOB-объект|varbinary(max)|  
|Boolean|bit|  
|CHAR|char;|  
|переменной типа char [*.. 8000]|varchar [*]|  
|переменной типа char [8001.. *]|varchar(max)|  
|char [*.. 8000]|char [*]|  
|char [8001.. *]|varchar(max)|  
|Символ|char;|  
|символ varying [*.. 8000]|varchar [*]|  
|символ varying [8001.. *]|varchar(max)|  
|символ [*.. 8000]|char [*]|  
|символ [8001.. *]|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|DEC [*.. \*]|DEC [*] [0]|  
|dec[*..\*][\*..\*]|dec[*][\*]|  
|Decimal|decimal[38][0]|  
|Decimal [*.. \*]|Decimal [*] [0]|  
|Decimal [*.. \*][\*.. \*]|Decimal [*] [\*]|  
|число двойной точности|число с плавающей запятой [53]|  
|Число с плавающей запятой|число с плавающей запятой [53]|  
|число с плавающей запятой [*.. 53]|число с плавающей запятой [*]|  
|число с плавающей запятой [54.. *]|число с плавающей запятой [53]|  
|int|int|  
|Целочисленный|int|  
|целое число со знаком [*.. \*]|числовой [*] [0]|  
|Long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [*.. 8000]|varbinary [*]|  
|Long raw [8001.. *]|varbinary(max)|  
|Национальный char|NCHAR|  
|Национальный char переменной [*.. 4000]|nvarchar [*]|  
|Национальный char переменной [4001.. *]|nvarchar(max)|  
|Национальный char [*.. 4000]|nchar [*]|  
|Национальный char [4001.. *]|nvarchar(max)|  
|символов национального алфавита|NCHAR|  
|национальных символов [*.. 4000]|nvarchar [*]|  
|национальных символов [4001.. *]|nvarchar(max)|  
|изменение символов национального алфавита [*.. 4000]|nvarchar [*]|  
|изменение символов национального алфавита [4001.. *]|nvarchar(max)|  
|Nchar|NCHAR|  
|nchar [*.. 4000]|nchar [*]|  
|nchar [4001.. *]|nvarchar(max)|  
|nchar varying [*.. 4000]|nvarchar [*]|  
|nchar varying [4001.. *]|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|Количество|число с плавающей запятой [53]|  
|Номер [*.. \*]|числовой [*]|  
|Номер [*.. \*][\*.. \*]|числовой [*] [\*]|  
|Числовой|numeric[38][0]|  
|числовые [*.. \*]|числовой [*]|  
|numeric[*..\*][\*..\*]|числовой [*] [\*]|  
|NVARCHAR2 [*.. 4000]|nvarchar [*]|  
|NVARCHAR2 [4001.. *]|nvarchar(max)|  
|pls_integer|int|  
|Необработанный [*.. 8000]|varbinary [*]|  
|Необработанный [8001.. *]|varbinary(max)|  
|Real|число с плавающей запятой [53]|  
|RowId|uniqueidentifier|  
|Signtype|smallint|  
|Smallint|smallint|  
|строки [*.. 8000]|varchar [*]|  
|string[8001..*]|varchar(max)|  
|TIMESTAMP|datetime2|  
|Отметка времени с местным часовым поясом|datetimeoffset|  
|Отметка времени с часовым поясом|datetimeoffset|  
|Отметка времени с местным часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Отметка времени с часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Отметка времени [*.. \*]|datetime2 [*]|  
|Urowid|uniqueidentifier|  
|urowid [*.. \*]|uniqueidentifier|  
|varchar [*.. 8000]|varchar [*]|  
|varchar [8001.. *]|varchar(max)|  
|VARCHAR2 [*.. 8000]|varchar [*]|  
|VARCHAR2 [8001.. *]|varcha(max)|  
|Xmltype|xml|  
  
## <a name="see-also"></a>См. также  
[Справочник по пользовательскому интерфейсу &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  

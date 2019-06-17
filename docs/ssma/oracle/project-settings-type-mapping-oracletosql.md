---
title: Параметры проекта (сопоставление типов) (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4bb8466e-2199-4f00-8513-b04e9586723d
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 449f1ecc2fbcc2f9e18ea24cb5bd42323bbf5ddc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62625888"
---
# <a name="project-settings-type-mapping-oracletosql"></a>Параметры проекта (сопоставление типов) (OracleToSQL)
На странице сопоставления типов **параметры проекта** диалоговое окно содержит настройки, установленные как SSMA преобразует типы данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.  
  
Страница сопоставления типов доступна в **параметры проекта** и **параметры проекта по умолчанию** диалоговым окнам.  
  
-   Чтобы указать параметры для всех будущих проектов SSMA на **средства** выберите в меню пункты **параметры проекта по умолчанию**, выберите тип проекта миграции, для которого требуются параметры для просмотра и изменения из **Целевой версии миграции** раскрывающийся список, а затем нажмите кнопку **сопоставления типов** в нижней части левой панели.  
  
-   Для задания параметров для текущего проекта на **средства** меню **параметры проекта**и нажмите кнопку **сопоставления типов** в нижней части левой панели.  
  
Чтобы указать параметры для текущего объекта или класса объектов, используйте **сопоставления типов** вкладки в окне первичной SSMA.  
  
## <a name="options"></a>Параметры  
В следующей таблице показаны **сопоставления типов** вкладке Параметры:  
  
**Исходный тип**  
Сопоставленный тип данных Oracle.  
  
**Тип целевого объекта**  
Целевой объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных для указанного типа данных Oracle.  
  
См. в таблицах в следующем разделе по умолчанию SSMA для Oracle сопоставления типов.  
  
**Добавить**  
Щелкните, чтобы добавить в список сопоставления типа данных.  
  
**Изменить**  
Щелкните, чтобы изменить тип данных выбранного в списке сопоставление.  
  
**Удалить**  
Щелкните, чтобы удалить сопоставление типов данных, выбранного в списке сопоставление.  
  
**Сброс до значений по умолчанию**  
Щелкните, чтобы сбросить список сопоставления типа по умолчанию SSMA.  
  
## <a name="default-type-mappings"></a>Сопоставления типов по умолчанию  
В SSMA для Oracle можно задать настраиваемые сопоставления типов для аргументов, столбцы, локальные переменные и возвращаемые значения. Сопоставление по умолчанию для аргументов и возвращаемых типов практически идентичны.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>По умолчанию тип аргумента и возвращают значение сопоставление типов  
Следующая таблица содержит сопоставление типов данных по умолчанию для аргументов и возвращаемых значений.  
  
|Тип данных Oracle|По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|число с плавающей запятой [53]|  
|binary_float|число с плавающей запятой [53]|  
|binary_integer|ssNoversion|  
|большой двоичный объект|varbinary(max)|  
|Логическое|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|character|varchar(max)|  
|character varying|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|Decimal|число с плавающей запятой [53]|  
|двойной точности|число с плавающей запятой [53]|  
|float|число с плавающей запятой [53]|  
|ssNoversion|ssNoversion|  
|integer|ssNoversion|  
|long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [\*.. 8000]<sup>*</sup>|varbinary [*]|  
|Long raw [8001..\*]<sup>*</sup>|varbinary(max)|  
|National char|nvarchar(max)|  
|National char varying|nvarchar(max)|  
|символов национального алфавита|nvarchar(max)|  
|изменение символов национального алфавита<sup>**</sup>|nvarchar(max)|  
|изменение символов национального алфавита<sup>*</sup>|nvarchar(max)|  
|nchar|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|number|число с плавающей запятой [53]|  
|NUMERIC|число с плавающей запятой [53]|  
|nvarchar2|nvarchar(max)|  
|pls_integer|ssNoversion|  
|raw|varbinary(max)|  
|real|число с плавающей запятой [53]|  
|RowId|UNIQUEIDENTIFIER|  
|Signtype|smallint|  
|smallint|smallint|  
|строка|varchar(max)|  
|TIMESTAMP|datetime2|  
|Метка времени с местным часовым поясом|datetimeoffset|  
|Метка времени с часовым поясом|datetimeoffset|  
|urowid|UNIQUEIDENTIFIER|  
|varchar|varchar(max)|  
|VARCHAR2|varchar(max)|  
|xmltype|Xml|  
  
<sup>*</sup> Применяется для возврата значения только сопоставления типов.  
  
<sup>**</sup> Применяется к аргумента только сопоставления типов.  
  
### <a name="default-column-type-mapping"></a>По умолчанию сопоставление типа столбца  
Следующая таблица содержит сопоставление типов по умолчанию для столбцов.  
  
|Тип данных Oracle|По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных|  
|--------------------|-------------------------------------------------------------------------|  
|BFILE|varbinary(max)|  
|binary_double|число с плавающей запятой [53]|  
|binary_float|число с плавающей запятой [53]|  
|большой двоичный объект|varbinary(max)|  
|char|char|  
|char varying [*.. \*]|varchar [*]|  
|char [*.. \*]|char [*]|  
|character|char|  
|Изменение символа [*.. \*]|varchar [*]|  
|символ [*.. \*]|char [*]|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|DEC [*.. \*]|DEC [*] [0]|  
|dec[*..\*][\*..\*]|DEC [*] [\*]|  
|Decimal|decimal[38][0]|  
|Decimal [*.. \*]|Decimal [*] [0]|  
|Decimal [*.. \*][\*.. \*]|Decimal [*] [\*]|  
|двойной точности|число с плавающей запятой [53]|  
|float|число с плавающей запятой [53]|  
|число с плавающей запятой [*.. 53]|в число с плавающей запятой [*]|  
|число с плавающей запятой [54.. *]|число с плавающей запятой [53]|  
|ssNoversion|ssNoversion|  
|integer|ssNoversion|  
|long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [*.. 8000]|varbinary [*]|  
|Long raw [8001.. *]|varbinary(max)|  
|Long varchar|varchar(max)|  
|Long [*.. 8000]|varchar [*]|  
|Long [8001.. *]|varchar(max)|  
|National char|nchar|  
|National char varying [*.. \*]|nvarchar [*]|  
|National char [*.. \*]|nchar [*]|  
|символов национального алфавита|nchar|  
|различных национальных символов [*.. \*]|nvarchar [*]|  
|символов национального алфавита [*.. \*]|nchar [*]|  
|nchar|nchar|  
|nchar [*]|nchar [*]|  
|NCLOB|nvarchar(max)|  
|number|число с плавающей запятой [53]|  
|Номер [*.. \*]|числовые [*]|  
|Номер [*.. \*][\*.. \*]|числовые [*] [\*]|  
|NUMERIC|NUMERIC|  
|числовые [*.. \*]|числовые [*]|  
|numeric[*..\*][\*..\*]|числовые [*] [\*]|  
|NVARCHAR2 [*.. \*]|nvarchar [*]|  
|необработанные [*.. \*]|varbinary [*]|  
|real|число с плавающей запятой [53]|  
|RowId|UNIQUEIDENTIFIER|  
|smallint|smallint|  
|TIMESTAMP|datetime2|  
|Метка времени с местным часовым поясом|datetimeoffset|  
|Метка времени с местным часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Метка времени с часовым поясом|datetimeoffset|  
|Метка времени с часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Метка времени [*.. \*]|datetime2 [*]|  
|urowid|UNIQUEIDENTIFIER|  
|urowid [*.. \*]|UNIQUEIDENTIFIER|  
|varchar [*.. \*]|varchar [*]|  
|VARCHAR2 [*.. \*]|varchar [*]|  
|xmltype|Xml|  
  
### <a name="default-local-variable-type-mapping"></a>Сопоставление по умолчанию тип локальной переменной  
Следующая таблица содержит сопоставление типов по умолчанию для локальных переменных.  
  
|Тип данных Oracle|По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных|  
|--------------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|число с плавающей запятой [53]|  
|binary_float|число с плавающей запятой [53]|  
|binary_interger|ssNoversion|  
|Blob|varbinary(max)|  
|Логическое значение|bit|  
|CHAR|char|  
|char varying [*.. 8000]|varchar [*]|  
|char varying [8001.. *]|varchar(max)|  
|char [*.. 8000]|char [*]|  
|char [8001.. *]|varchar(max)|  
|Символ|char|  
|Изменение символа [*.. 8000]|varchar [*]|  
|Изменение символа [8001.. *]|varchar(max)|  
|символ [*.. 8000]|char [*]|  
|символ [8001.. *]|varchar(max)|  
|CLOB|varchar(max)|  
|date|datetime2 [0]|  
|dec|dec[38][0]|  
|DEC [*.. \*]|DEC [*] [0]|  
|dec[*..\*][\*..\*]|DEC [*] [\*]|  
|Decimal|decimal[38][0]|  
|Decimal [*.. \*]|Decimal [*] [0]|  
|Decimal [*.. \*][\*.. \*]|Decimal [*] [\*]|  
|двойной точности|число с плавающей запятой [53]|  
|float|число с плавающей запятой [53]|  
|число с плавающей запятой [*.. 53]|в число с плавающей запятой [*]|  
|число с плавающей запятой [54.. *]|число с плавающей запятой [53]|  
|int|ssNoversion|  
|Целочисленный|ssNoversion|  
|целое число [*.. \*]|числовые [*] [0]|  
|Long|varchar(max)|  
|Long raw|varbinary(max)|  
|Long raw [*.. 8000]|varbinary [*]|  
|Long raw [8001.. *]|varbinary(max)|  
|National char|nchar|  
|National char varying [*.. 4000]|nvarchar [*]|  
|National char varying [4001.. *]|nvarchar(max)|  
|National char [*.. 4000]|nchar [*]|  
|National char [4001.. *]|nvarchar(max)|  
|символов национального алфавита|nchar|  
|символов национального алфавита [*.. 4000]|nvarchar [*]|  
|символов национального алфавита [4001.. *]|nvarchar(max)|  
|различных национальных символов [*.. 4000]|nvarchar [*]|  
|различных национальных символов [4001.. *]|nvarchar(max)|  
|Nchar|nchar|  
|nchar [*.. 4000]|nchar [*]|  
|nchar [4001.. *]|nvarchar(max)|  
|nchar varying [*.. 4000]|nvarchar [*]|  
|nchar varying [4001.. *]|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|Number|число с плавающей запятой [53]|  
|Номер [*.. \*]|числовые [*]|  
|Номер [*.. \*][\*.. \*]|числовые [*] [\*]|  
|Numeric|numeric[38][0]|  
|числовые [*.. \*]|числовые [*]|  
|numeric[*..\*][\*..\*]|числовые [*] [\*]|  
|NVARCHAR2 [*.. 4000]|nvarchar [*]|  
|nvarchar2[4001..*]|nvarchar(max)|  
|pls_integer|ssNoversion|  
|необработанные [*.. 8000]|varbinary [*]|  
|необработанные [8001.. *]|varbinary(max)|  
|Real|число с плавающей запятой [53]|  
|Rowid|UNIQUEIDENTIFIER|  
|Signtype|smallint|  
|Smallint|smallint|  
|строки [*.. 8000]|varchar [*]|  
|string[8001..*]|varchar(max)|  
|TIMESTAMP|datetime2|  
|Метка времени с местным часовым поясом|datetimeoffset|  
|Метка времени с часовым поясом|datetimeoffset|  
|Метка времени с местным часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Метка времени с часовым поясом [*.. \*]|DateTimeOffset [*]|  
|Метка времени [*.. \*]|datetime2 [*]|  
|urowid|UNIQUEIDENTIFIER|  
|urowid [*.. \*]|UNIQUEIDENTIFIER|  
|varchar [*.. 8000]|varchar [*]|  
|varchar [8001.. *]|varchar(max)|  
|VARCHAR2 [*.. 8000]|varchar [*]|  
|varchar2[8001..*]|varcha(max)|  
|xmltype|Xml|  
  
## <a name="see-also"></a>См. также  
[Справочник по пользовательскому интерфейсу &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  

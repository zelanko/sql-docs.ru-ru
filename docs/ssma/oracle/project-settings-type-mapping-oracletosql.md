---
title: Параметры проекта (сопоставление типов) (OracleToSQL) | Документация Майкрософт
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4bb8466e-2199-4f00-8513-b04e9586723d
author: nahk-ivanov
ms.author: alexiva
manager: alexiva
ms.openlocfilehash: ab1b453fb85d7b9c6ee0cf9a271c1af55a337b4a
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/07/2020
ms.locfileid: "87933185"
---
# <a name="project-settings-type-mapping-oracletosql"></a>Параметры проекта (сопоставление типов) (OracleToSQL)
Страница Сопоставление типов диалогового окна **Параметры проекта** содержит параметры, которые настраивают, как SSMA преобразует типы данных Oracle в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типы данных.  
  
Страница Сопоставление типов доступна в диалоговых окнах **Параметры проекта** и **Параметры проекта по умолчанию** .  
  
-   Чтобы указать параметры для всех будущих проектов SSMA, в меню **Сервис** щелкните **Параметры проекта по умолчанию**, выберите тип проекта миграции, для которого необходимо просмотреть или изменить параметры в раскрывающемся списке **версия целевого объекта миграции** , а затем щелкните **Сопоставление типов** в нижней части левой панели.  
  
-   Чтобы указать параметры для текущего проекта, в меню **Сервис** выберите пункт **Параметры проекта**, а затем щелкните **Сопоставление типов** в нижней части левой панели.  
  
Чтобы задать параметры для текущего объекта или класса объектов, используйте вкладку **Сопоставление типов** в главном окне SSMA.  
  
## <a name="options"></a>Параметры  
В следующей таблице показаны параметры вкладки **Сопоставление типов** .  
  
**Тип источника**  
Сопоставленный тип данных Oracle.  
  
**Тип целевого объекта**  
Целевой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных для указанного типа данных Oracle.  
  
См. таблицы в следующем разделе для сопоставления типов SSMA по умолчанию для Oracle.  
  
**Добавление**  
Нажмите, чтобы добавить тип данных в список сопоставления.  
  
**Edit** (Изменение)  
Нажмите, чтобы изменить выбранный тип данных в списке сопоставление.  
  
**Удалить**  
Нажмите, чтобы удалить выбранное сопоставление типа данных из списка сопоставления.  
  
**По умолчанию**  
Нажмите, чтобы сбросить список сопоставления типов к значениям по умолчанию SSMA.  
  
## <a name="default-type-mappings"></a>Сопоставления типов по умолчанию  
В SSMA для Oracle можно задать пользовательские сопоставления типов для аргументов, столбцов, локальных переменных и возвращаемых значений. Сопоставление по умолчанию для аргументов и возвращаемых типов практически идентично.  
  
### <a name="default-argument-type-and-return-value-type-mapping"></a>Сопоставление типа аргумента по умолчанию и типа возвращаемого значения  
Следующая таблица содержит сопоставление типов данных по умолчанию для аргументов и возвращаемых значений.  
  
|Тип данных Oracle|Тип данных по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|--------------------|-------------------------------------------------------------------------|  
|bСведения|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_integer|int|  
|большой двоичный объект|varbinary(max)|  
|Логическое|bit|  
|char|varchar(max)|  
|char varying|varchar(max)|  
|character|varchar(max)|  
|character varying|varchar(max)|  
|CLOB|varchar(max)|  
|Дата|datetime2 [0]|  
|dec|Dec [38] [0]|  
|Decimal|float [53]|  
|double precision|float [53]|  
|FLOAT|float [53]|  
|int|int|  
|целое число|INT|  
|long|varchar(max)|  
|Long RAW|varbinary(max)|  
|Long RAW [ \* .. 8000]<sup>*</sup>|varbinary [*]|  
|Long RAW [8001.. \* ]<sup>*</sup>|varbinary(max)|  
|Национальный знак|nvarchar(max)|  
|разные национальные знаки|nvarchar(max)|  
|Национальный символ|nvarchar(max)|  
|изменение национального алфавита<sup>**</sup>|nvarchar(max)|  
|изменение национального алфавита<sup>*</sup>|nvarchar(max)|  
|nchar|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|число|float [53]|  
|NUMERIC|float [53]|  
|nvarchar2|nvarchar(max)|  
|pls_integer|int|  
|raw|varbinary(max)|  
|real|float [53]|  
|ROWID|UNIQUEIDENTIFIER|  
|сигнтипе|smallint|  
|smallint|smallint|  
|строка|varchar(max)|  
|TIMESTAMP|datetime2|  
|Метка времени с местным часовым поясом|datetimeoffset|  
|Метка времени с часовым поясом|datetimeoffset|  
|urowid|UNIQUEIDENTIFIER|  
|varchar|varchar(max)|  
|VARCHAR2|varchar(max)|  
|XmlType|Xml|  
  
<sup>*</sup>Применяется только к сопоставлению типов возвращаемых значений.  
  
<sup>**</sup>Применяется только к сопоставлению типов аргументов.  
  
### <a name="default-column-type-mapping"></a>Сопоставление типов столбцов по умолчанию  
Следующая таблица содержит сопоставление типов по умолчанию для столбцов.  
  
|Тип данных Oracle|Тип данных по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|--------------------|-------------------------------------------------------------------------|  
|bСведения|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|большой двоичный объект|varbinary(max)|  
|char|char|  
|различные знаки [*.. \* ]|varchar [*]|  
|Char [*.. \* ]|Char [*]|  
|character|char|  
|Разное символов [*.. \* ]|varchar [*]|  
|символ [*.. \* ]|Char [*]|  
|CLOB|varchar(max)|  
|Дата|datetime2 [0]|  
|dec|Dec [38] [0]|  
|Dec [*.. \* ]|Dec [*] [0]|  
|Dec [*.. \* ] [\*..\*]|Dec [*] [ \* ]|  
|Decimal|Decimal [38] [0]|  
|Decimal [*.. \* ]|Decimal [*] [0]|  
|Decimal [*.. \* ] [\*..\*]|Decimal [*] [ \* ]|  
|double precision|float [53]|  
|FLOAT|float [53]|  
|float [*.. 53]|float [*]|  
|float [54.. *]|float [53]|  
|int|int|  
|целое число|INT|  
|long|varchar(max)|  
|Long RAW|varbinary(max)|  
|Long RAW [*.. 8000]|varbinary [*]|  
|Long RAW [8001.. *]|varbinary(max)|  
|long varchar|varchar(max)|  
|Long [*.. 8000]|varchar [*]|  
|Long [8001.. *]|varchar(max)|  
|Национальный знак|nchar|  
|Национальная кодировка [*.. \* ]|nvarchar [*]|  
|Национальный знак [*.. \* ]|nchar [*]|  
|Национальный символ|nchar|  
|Национальная буква [*.. \* ]|nvarchar [*]|  
|Национальный символ [*.. \* ]|nchar [*]|  
|nchar|nchar|  
|nchar [*]|nchar [*]|  
|NCLOB|nvarchar(max)|  
|число|float [53]|  
|Number [*.. \* ]|numeric [*]|  
|Number [*.. \* ] [\*..\*]|numeric [*] [ \* ]|  
|NUMERIC|NUMERIC|  
|numeric [*.. \* ]|numeric [*]|  
|numeric [*.. \* ] [\*..\*]|numeric [*] [ \* ]|  
|NVARCHAR2 [*.. \* ]|nvarchar [*]|  
|RAW [*.. \* ]|varbinary [*]|  
|real|float [53]|  
|ROWID|UNIQUEIDENTIFIER|  
|smallint|smallint|  
|TIMESTAMP|datetime2|  
|Метка времени с местным часовым поясом|datetimeoffset|  
|Метка времени с местным часовым поясом [*.. \* ]|DateTimeOffset [*]|  
|Метка времени с часовым поясом|datetimeoffset|  
|Метка времени с часовым поясом [*.. \* ]|DateTimeOffset [*]|  
|timestamp [*.. \* ]|datetime2 [*]|  
|Urowid|UNIQUEIDENTIFIER|  
|urowid [*.. \* ]|UNIQUEIDENTIFIER|  
|varchar [*.. \* ]|varchar [*]|  
|VARCHAR2 [*.. \* ]|varchar [*]|  
|XmlType|Xml|  
  
### <a name="default-local-variable-type-mapping"></a>Сопоставление типов локальных переменных по умолчанию  
Следующая таблица содержит сопоставление типов по умолчанию для локальных переменных.  
  
|Тип данных Oracle|Тип данных по умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|--------------------|-------------------------------------------------------------------------|  
|Bfile|varbinary(max)|  
|binary_double|float [53]|  
|binary_float|float [53]|  
|binary_interger|int|  
|BLOB-объект|varbinary(max)|  
|Логическое|bit|  
|Char|char|  
|различные знаки [*.. 8000]|varchar [*]|  
|изменение типа char [8001.. *]|varchar(max)|  
|Char [*.. 8000]|Char [*]|  
|Char [8001.. *]|varchar(max)|  
|Знак|char|  
|Разное символов [*.. 8000]|varchar [*]|  
|разное начертание [8001.. *]|varchar(max)|  
|символ [*.. 8000]|Char [*]|  
|Character [8001.. *]|varchar(max)|  
|CLOB|varchar(max)|  
|Дата|datetime2 [0]|  
|dec|Dec [38] [0]|  
|Dec [*.. \* ]|Dec [*] [0]|  
|Dec [*.. \* ] [\*..\*]|Dec [*] [ \* ]|  
|Decimal|Decimal [38] [0]|  
|Decimal [*.. \* ]|Decimal [*] [0]|  
|Decimal [*.. \* ] [\*..\*]|Decimal [*] [ \* ]|  
|double precision|float [53]|  
|Float|float [53]|  
|float [*.. 53]|float [*]|  
|float [54.. *]|float [53]|  
|Int|int|  
|Целое число|int|  
|Integer [*.. \* ]|numeric [*] [0]|  
|Long|varchar(max)|  
|Long RAW|varbinary(max)|  
|Long RAW [*.. 8000]|varbinary [*]|  
|Long RAW [8001.. *]|varbinary(max)|  
|Национальный знак|nchar|  
|Национальная кодировка [*.. 4000]|nvarchar [*]|  
|Национальный символ [4001.. *]|nvarchar(max)|  
|Национальный знак [*.. 4000]|nchar [*]|  
|Национальный символ [4001.. *]|nvarchar(max)|  
|Национальный символ|nchar|  
|Национальный символ [*.. 4000]|nvarchar [*]|  
|Национальный символ [4001.. *]|nvarchar(max)|  
|разный национальный символ [*.. 4000]|nvarchar [*]|  
|Национальный символ, Разное [4001.. *]|nvarchar(max)|  
|Nchar|nchar|  
|nchar [*.. 4000]|nchar [*]|  
|nchar [4001.. *]|nvarchar(max)|  
|изменение типа nchar [*.. 4000]|nvarchar [*]|  
|изменение типа nchar [4001.. *]|nvarchar(max)|  
|NCLOB|nvarchar(max)|  
|Число|float [53]|  
|Number [*.. \* ]|numeric [*]|  
|Number [*.. \* ] [\*..\*]|numeric [*] [ \* ]|  
|Числовой|numeric [38] [0]|  
|numeric [*.. \* ]|numeric [*]|  
|numeric [*.. \* ] [\*..\*]|numeric [*] [ \* ]|  
|nvarchar2[*.. 4000]|nvarchar [*]|  
|NVARCHAR2 [4001.. *]|nvarchar(max)|  
|pls_integer|int|  
|RAW [*.. 8000]|varbinary [*]|  
|RAW [8001.. *]|varbinary(max)|  
|Real|float [53]|  
|Rowid|UNIQUEIDENTIFIER|  
|сигнтипе|smallint|  
|Smallint|smallint|  
|строка [*.. 8000]|varchar [*]|  
|String [8001.. *]|varchar(max)|  
|TIMESTAMP|datetime2|  
|Метка времени с местным часовым поясом|datetimeoffset|  
|Метка времени с часовым поясом|datetimeoffset|  
|Метка времени с местным часовым поясом [*.. \* ]|DateTimeOffset [*]|  
|Метка времени с часовым поясом [*.. \* ]|DateTimeOffset [*]|  
|timestamp [*.. \* ]|datetime2 [*]|  
|Urowid|UNIQUEIDENTIFIER|  
|urowid [*.. \* ]|UNIQUEIDENTIFIER|  
|varchar [*.. 8000]|varchar [*]|  
|varchar [8001.. *]|varchar(max)|  
|VARCHAR2 [*.. 8000]|varchar [*]|  
|VARCHAR2 [8001.. *]|Варча (max)|  
|XmlType|Xml|  
  
## <a name="see-also"></a>См. также:  
[Справочник по пользовательскому интерфейсу &#40;OracleToSQL&#41;](../../ssma/oracle/user-interface-reference-oracletosql.md)  
  

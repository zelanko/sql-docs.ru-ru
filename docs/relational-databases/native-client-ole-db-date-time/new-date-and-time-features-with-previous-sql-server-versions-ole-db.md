---
title: Особенности даты и времени OLE DB с предыдущими версиями серверов S'L
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
author: markingmyname
ms.author: maghan
ms.custom: seo-dt-2019
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: a90863fb061912dd0a6c44fe23ba2baa402662c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301027"
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Новые функции даты и времени с предыдущими версиями SQL Server (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Эта тема описывает ожидаемое поведение, когда клиентское приложение, использующее [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширенные функции даты и времени, общается с версией раньше, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], и когда клиент, компилированный с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client раньше, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] отправляет команды на сервер, который поддерживает расширенные функции даты и времени.  
  
## <a name="down-level-client-behavior"></a>Работа в клиентах низкого уровня  
 Клиентские приложения, которые [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] используют версию Native Client раньше, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] видят новые типы дат/времени как столбцы **nvarchar.** Содержимое столбца представлено литералом. Для получения дополнительной информации см. [Data Type Support for OLE DB Date and Time Improvements](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md) Размер столбца представляет максимальную длину литерала для точности, указанной для столбца.  
  
 ApIs каталога будет возвращать метаданные в соответствии с кодом типа данных нисходящем, возвращенным клиенту (например, **nvarchar)** и связанному представлению на уровне нисходящем (например, соответствующему буквальному формату). Тем не менее, будет возвращено реальное имя типа данных [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 Когда клиентское приложение ниже уровня [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] работает на (или позже) сервере, на котором были внесены изменения схемы к типам дат/времени, ожидаемое поведение таково:  
  
|Тип клиента OLE DB|Тип SQL Server 2005|Тип SQL Server 2008 (или более поздних версий)|Преобразование результата (сервер-клиент)|Преобразование параметра (клиент-сервер)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|Datetime|Дата|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Поля времени устанавливаются в нули.|IRowsetChange не удастся из-за усечения строки, если временное поле не является нулевым.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Поля даты устанавливаются в текущую дату.|IRowsetChange не удастся из-за усечения строки, если дробные секунды не равны нулю.<br /><br /> Дата не учитывается.|  
|DBTYPE_DBTIME||Time(7)|Неудачи - недействительное время буквальное.|OK|  
|DBTYPE_DBTIMESTAMP|||Неудачи - недействительное время буквальное.|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(3)|OK|OK|  
|DBTYPE_DBTIMESTAMP||Datetime2(7)|OK|OK|  
|DBTYPE_DBDATE|Smalldatetime|Дата|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Поля времени устанавливаются в нули.|IRowsetChange не удастся из-за усечения строки, если временное поле не является нулевым.|  
|DBTYPE_DBTIME||Time(0)|OK|OK|  
|DBTYPE_DBTIMESTAMP|||Поля даты устанавливаются в текущую дату.|IRowsetChange не удастся из-за усечения строки, если дробные секунды не равны нулю.<br /><br /> Дата не учитывается.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|OK|OK|  
  
 Значение «ОК» означает, что если код работал в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], то он должен работать и в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (и более поздних версиях).  
  
 Учтены только следующие типичные изменения схемы.  
  
-   Использование нового типа, когда логически приложению необходимо только значение даты или времени. Однако приложение было вынуждено использовать **время даты** или **небольшое время,** поскольку отдельные типы дат и времени отсутствовали.  
  
-   Использование нового типа для получения долей секунд c более высокой точностью.  
  
-   Переключение на **datetime2,** потому что это предпочтительный тип данных для даты и времени.  
  
 Приложения, которые используют метаданные сервера, полученные через ICommandWithParameters::GetParameterInfo или строки схемы для набора информации о типе параметра через ICommandWithParameters::SetParameterInfo не удастся во время конверсий клиента, где строка представления типа источника больше, чем строка представления типа назначения. Например, если привязка клиента использует DBTYPE_DBTIMESTAMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и столбец сервера является датой, Native Client преобразует значение в "yyyy-dd-mm hh:mm:ss.fff", но метаданные сервера будут возвращены как **nvarchar (10)**. В результате переполнение приведет к ошибке DBSTATUS_E_CATCONVERTVALUE. Аналогичные проблемы возникают с преобразованиями данных IRowsetChange, поскольку метаданные строки устанавливаются из метаданных набора результатов.  
  
### <a name="parameter-and-rowset-metadata"></a>Метаданные параметров и наборов строк  
 В этом разделе описаны метаданные по параметрам, столбики результатов и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] строки схем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]для клиентов, которые компилируются с версией Native Client раньше, чем .  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Структура DBPARAMINFO возвращает следующую информацию через параметр *prgParamInfo:*  
  
|Тип параметра|wType|ulParamSize|bPrecision|bScale|  
|--------------------|-----------|-----------------|----------------|------------|  
|Дата|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
 Обратите внимание, что некоторые из этих диапазонов значений не являются непрерывными, например в последовательности 8, 10… 16 отсутствует значение 9. Это следствие добавления десятичной запятой, когда точность в долях секунды выше нуля.  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Возвращаются следующие столбцы.  
  
|Тип столбца|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|Дата|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8, 10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 Структура DBCOLUMNINFO возвращает следующие данные.  
  
|Тип параметра|wType|ulColumnSize|bPrecision|bScale|  
|--------------------|-----------|------------------|----------------|------------|  
|Дата|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
### <a name="schema-rowsets"></a>Наборы строк схемы  
 В этом разделе рассматриваются метаданные для параметров, результирующих столбцов и наборов строк схемы для новых типов данных. Эта информация полезна, у вас есть [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] клиент-провайдер, разработанный с помощью инструментов раньше, чем Родной Клиент.  
  
#### <a name="columns-rowset"></a>COLUMNS, набор строк  
 Для типов даты-времени возвращаются значения следующих столбцов.  
  
|Тип столбца|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|Дата|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|NULL|  
  
#### <a name="procedure_parameters-rowset"></a>Набор строк PROCEDURE_PARAMETERS  
 Для типов даты-времени возвращаются значения следующих столбцов.  
  
|Тип столбца|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|Дата|DBTYPE_WSTR|10|20|Дата|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|DATETIME|DBTYPE_DBTIMESTAMP|NULL|NULL|DATETIME|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|datetimeoffset|  
  
#### <a name="provider_types-rowset"></a>Набор строк PROVIDER_TYPES  
 Для типов даты-времени возвращаются следующие строки:  
  
|Тип -><br /><br /> Столбец|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_WSTR|DBTYPE_WSTR|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_WSTR|DBTYPE_WSTR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|'|'|'|'|'|'|  
|LITERAL_SUFFIX|'|'|'|'|'|'|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|Дата|time|smalldatetime|DATETIME|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_TRUE|VARIANT_FALSE|VARIANT_FALSE|  
|IS_FIXEDLENGTH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
  
## <a name="down-level-server-behavior"></a>Работа сервера низкого уровня  
 При подключении к серверу [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]более ранней версии, чем, любая попытка использовать новые имена типов сервера (например, с ICommandWithParameters::SetParameterInfo или ITableDefinition::CreateTable) приведет к DB_E_BADTYPENAME.  
  
 Если новые типы привязываются к параметрам или результатам без указания имени типа и новый тип неявным образом указывает на серверный тип данных либо отсутствует допустимое преобразование из серверного типа данных в клиентский, то возвращается ошибка DB_E_ERRORSOCCURRED, а DBBINDSTATUS_UNSUPPORTED_CONVERSION устанавливается в состояние привязки для метода доступа, используемого Execute.  
  
 Если существует поддерживаемое клиентское преобразование из типа буфера в серверный тип данных для той версии сервера, с которым установлено соединение, то могут быть использованы все типы данных буфера клиента. В этом контексте *тип сервера* означает тип, указанный ICommandWithParameters::SetParameterInfo, или подразумевается типом буфера, если ICommandWithParameters::SetParameterInfo не был вызван. Это означает, что DBTYPE_DBTIME2 и DBTYPE_DBTIMESTAMPOFFSET могут быть использованы с серверами низкого уровня или при DataTypeCompatibility=80, если клиентское преобразование к поддерживаемому серверному типу данных выполнено успешно. Конечно, если обнаружен неверный серверный тип данных, то сервер может сообщить об ошибке, если не удается выполнить неявное преобразование к действительному серверному типу данных.  
  
## <a name="ssprop_init_datatypecompatibility-behavior"></a>Поведение SSPROP_INIT_DATATYPECOMPATIBILITY  
 Когда SSPROP_INIT_DATATYPECOMPATIBILITY настроена на SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000, новые типы дат/времени и связанные с ними метаданные появляются для клиентов, как они появляются для клиентов н.ф., как описано в [массовых изменениях копирования для увеличенных типов дат и времени &#40;OLE DB и ODBC&#41;. ](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
  
## <a name="comparability-for-irowsetfind"></a>Сравнимость для IRowsetFind  
 Все операторы сравнения разрешены для новых типов данных даты-времени, так как они отображаются как строковые типы, а не типы даты-времени.  
  
## <a name="see-also"></a>См. также:  
 [Улучшения функций даты и времени &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  

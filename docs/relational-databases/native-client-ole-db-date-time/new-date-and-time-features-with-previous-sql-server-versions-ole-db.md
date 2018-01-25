---
title: "Новых функций даты и времени с предыдущими версиями SQL Server (OLE DB) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 96976bac-018c-47cc-b1b2-fa9605eb55e5
caps.latest.revision: "27"
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 63d848005d0a1745070caf209f52f49dd80db1d2
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="new-date-and-time-features-with-previous-sql-server-versions-ole-db"></a>Новых функций даты и времени с предыдущими версиями SQL Server (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В этом разделе описывается ожидаемое поведение клиентского приложения, использующего улучшение типы даты и времени компоненты, взаимодействующие с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] более раннюю, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]и когда клиент, скомпилированный с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client раньше [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] отправляет команды на сервер, поддерживающий улучшенные функции даты и времени.  
  
## <a name="down-level-client-behavior"></a>Работа в клиентах низкого уровня  
 Клиентские приложения, использующие версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] см. типы даты или как **nvarchar** столбцов. Содержимое столбца представлено литералом. Дополнительные сведения см. раздел «Данных форматов: строки и литералы» [поддержка типов данных даты OLE DB и улучшения времени](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md). Размер столбца представляет максимальную длину литерала для точности, указанной для столбца.  
  
 API-интерфейсы каталога возвращают метаданные, согласующиеся с кодом типа данных низкого уровня, возвращаемый клиенту (например, **nvarchar**) и связанные представлением низкого уровня (например, соответствующий формат литерала). Тем не менее, будет возвращено реальное имя типа данных [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
 При запуске приложения клиента нижнего уровня на [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) — ожидаемое поведение сервера, на какие изменения схемы для даты и времени были внесены типы, следующим образом:  
  
|Тип клиента OLE DB|Тип SQL Server 2005|Тип SQL Server 2008 (или более поздних версий)|Преобразование результата (сервер-клиент)|Преобразование параметра (клиент-сервер)|  
|------------------------|--------------------------|---------------------------------------|--------------------------------------------|-----------------------------------------------|  
|DBTYPE_DBDATE|DateTime|Дата|ОК|ОК|  
|DBTYPE_DBTIMESTAMP|||Поля времени устанавливаются в нули.|IRowsetChange завершится ошибкой из-за усечения строки, если поля времени не равно нулю.|  
|DBTYPE_DBTIME||Time(0)|ОК|ОК|  
|DBTYPE_DBTIMESTAMP|||Поля даты устанавливаются в текущую дату.|IRowsetChange завершится ошибкой из-за усечения строки, если доли секунды не равны нулю.<br /><br /> Дата не учитывается.|  
|DBTYPE_DBTIME||Time(7)|Ошибка — недопустимый литерал времени.|ОК|  
|DBTYPE_DBTIMESTAMP|||Ошибка — недопустимый литерал времени.|ОК|  
|DBTYPE_DBTIMESTAMP||Datetime2(3)|ОК|ОК|  
|DBTYPE_DBTIMESTAMP||Datetime2(7)|ОК|ОК|  
|DBTYPE_DBDATE|Smalldatetime|Дата|ОК|ОК|  
|DBTYPE_DBTIMESTAMP|||Поля времени устанавливаются в нули.|IRowsetChange завершится ошибкой из-за усечения строки, если поля времени не равно нулю.|  
|DBTYPE_DBTIME||Time(0)|ОК|ОК|  
|DBTYPE_DBTIMESTAMP|||Поля даты устанавливаются в текущую дату.|IRowsetChange завершится ошибкой из-за усечения строки, если доли секунды не равны нулю.<br /><br /> Дата не учитывается.|  
|DBTYPE_DBTIMESTAMP||Datetime2(0)|ОК|ОК|  
  
 Значение «ОК» означает, что если код работал в [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], то он должен работать и в [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (и более поздних версиях).  
  
 Учтены только следующие типичные изменения схемы.  
  
-   Использование нового типа, когда логически приложению необходимо только значение даты или времени. Тем не менее, приложение должно использовать **datetime** или **smalldatetime** так как типы отдельные даты и времени были недоступны.  
  
-   Использование нового типа для получения долей секунд c более высокой точностью.  
  
-   Переключение на **datetime2** так, как это предпочтительный тип данных даты и времени.  
  
 Приложения, использующие сервер метаданные, полученные через наборы строк ICommandWithParameters::GetParameterInfo или схемы для задания сведений о типах параметров через ICommandWithParameters::SetParameterInfo завершится ошибкой при клиентских преобразований где строка представление типа источника больше, чем строковое представление типа назначения. Например, если привязка клиента использует DBTYPE_DBTIMESTAMP, а столбец сервера содержит дату [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client будет преобразовать значение «мм дд гггг чч:мм:сс.мс», но метаданные сервера возвращаются как **nvarchar(10)**. В результате переполнение приведет к ошибке DBSTATUS_E_CATCONVERTVALUE. Аналогичные проблемы возникают при преобразовании данных, IRowsetChange, так как метаданные наборов строк присваиваются из метаданных результирующего набора.  
  
### <a name="parameter-and-rowset-metadata"></a>Метаданные параметров и наборов строк  
 В этом разделе описаны метаданные для параметров, столбцов результатов и наборы строк схемы для клиентов, которые были скомпилированы с помощью версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
#### <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Структура DBPARAMINFO возвращает следующие данные через *prgParamInfo* параметр:  
  
|Тип параметра|wType|ulParamSize|bPrecision|bScale|  
|--------------------|-----------|-----------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
 Обратите внимание, что некоторые из этих диапазонов значений не являются непрерывными, например в последовательности 8, 10… 16 отсутствует значение 9. Это следствие добавления десятичной запятой, когда точность в долях секунды выше нуля.  
  
#### <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 Возвращаются следующие столбцы.  
  
|Тип столбца|DBCOLUMN_TYPE|DBCOLUMN_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|  
|-----------------|--------------------|--------------------------|-------------------------|--------------------------------------------------|  
|date|DBTYPE_WSTR|10|NULL|NULL|  
|time|DBTYPE_WSTR|8, 10..16|NULL|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|NULL|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|NULL|NULL|  
  
#### <a name="columnsinfogetcolumninfo"></a>ColumnsInfo::GetColumnInfo  
 Структура DBCOLUMNINFO возвращает следующие данные.  
  
|Тип параметра|wType|ulColumnSize|bPrecision|bScale|  
|--------------------|-----------|------------------|----------------|------------|  
|date|DBTYPE_WSTR|10|~0|~0|  
|time(1..7)|DBTYPE_WSTR|8, 10..16|~0|~0|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|  
|datetime2|DBTYPE_WSTR|19,21..27|~0|~0|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|~0|~0|  
  
### <a name="schema-rowsets"></a>Наборы строк схемы  
 В этом разделе рассматриваются метаданные для параметров, результирующих столбцов и наборов строк схемы для новых типов данных. Эта информация полезна является имеется поставщик клиента, разработанный с использованием средств более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
#### <a name="columns-rowset"></a>COLUMNS, набор строк  
 Для типов даты-времени возвращаются значения следующих столбцов.  
  
|Тип столбца|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|DATETIME_PRECISION|  
|-----------------|----------------|--------------------------------|------------------------------|-------------------------|  
|date|DBTYPE_WSTR|10|20|NULL|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|NULL|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|0|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|3|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|NULL|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|NULL|  
  
#### <a name="procedureparameters-rowset"></a>Набор строк PROCEDURE_PARAMETERS  
 Для типов даты-времени возвращаются значения следующих столбцов.  
  
|Тип столбца|DATA_TYPE|CHARACTER_MAXIMUM_LENGTH|CHARACTER_OCTET_LENGTH|TYPE_NAME<br /><br /> LOCAL_TYPE_NAME|  
|-----------------|----------------|--------------------------------|------------------------------|--------------------------------------|  
|date|DBTYPE_WSTR|10|20|date|  
|time|DBTYPE_WSTR|8, 10..16|16,20..32|time|  
|smalldatetime|DBTYPE_DBTIMESTAMP|NULL|NULL|smalldatetime|  
|datetime|DBTYPE_DBTIMESTAMP|NULL|NULL|datetime|  
|datetime2|DBTYPE_WSTR|19,21..27|38,42..54|datetime2|  
|datetimeoffset|DBTYPE_WSTR|26,28..34|52, 56..68|datetimeoffset|  
  
#### <a name="providertypes-rowset"></a>Набор строк PROVIDER_TYPES  
 Для типов даты-времени возвращаются следующие строки:  
  
|Тип -><br /><br /> Столбец|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|--------------------------|----------|----------|-------------------|--------------|---------------|--------------------|  
|TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|DATA_TYPE|DBTYPE_WSTR|DBTYPE_WSTR|DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|DBTYPE_WSTR|DBTYPE_WSTR|  
|COLUMN_SIZE|10|16|16|23|27|34|  
|LITERAL_PREFIX|‘|‘|‘|‘|‘|‘|  
|LITERAL_SUFFIX|‘|‘|‘|‘|‘|‘|  
|CREATE_PARAMS|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_NULLABLE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|VARIANT_TRUE|  
|CASE_SENSITIVE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|DB_SEARCHABLE|  
|UNSIGNED_ATTRIBUTE|NULL|NULL|NULL|NULL|NULL|NULL|  
|FIXED_PREC_SCALE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|AUTO_UNIQUE_VALUE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|LOCAL_TYPE_NAME|date|time|smalldatetime|datetime|datetime2|datetimeoffset|  
|MINIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|MAXIMUM_SCALE|NULL|NULL|NULL|NULL|NULL|NULL|  
|GUID|NULL|NULL|NULL|NULL|NULL|NULL|  
|TYPELIB|NULL|NULL|NULL|NULL|NULL|NULL|  
|VERSION|NULL|NULL|NULL|NULL|NULL|NULL|  
|IS_LONG|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
|BEST_MATCH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_TRUE|VARIANT_FALSE|VARIANT_FALSE|  
|IS_FIXEDLENGTH|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|VARIANT_FALSE|  
  
## <a name="down-level-server-behavior"></a>Работа сервера низкого уровня  
 При подключении к серверу более ранней версии, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], любые попытки использовать новых имен серверных типов (например, с помощью ICommandWithParameters::SetParameterInfo или ITableDefinition::CreateTable) приведет к ошибке DB_E_BADTYPENAME.  
  
 Если новые типы привязываются к параметрам или результатам без указания имени типа и новый тип неявным образом указывает на серверный тип данных либо отсутствует допустимое преобразование из серверного типа данных в клиентский, то возвращается ошибка DB_E_ERRORSOCCURRED, а DBBINDSTATUS_UNSUPPORTED_CONVERSION устанавливается в состояние привязки для метода доступа, используемого Execute.  
  
 Если существует поддерживаемое клиентское преобразование из типа буфера в серверный тип данных для той версии сервера, с которым установлено соединение, то могут быть использованы все типы данных буфера клиента. В этом контексте *тип сервера* означает тип данных, заданные ICommandWithParameters::SetParameterInfo или по типу буфера по умолчанию, если не был вызван ICommandWithParameters::SetParameterInfo. Это означает, что DBTYPE_DBTIME2 и DBTYPE_DBTIMESTAMPOFFSET могут быть использованы с серверами низкого уровня или при DataTypeCompatibility=80, если клиентское преобразование к поддерживаемому серверному типу данных выполнено успешно. Конечно, если обнаружен неверный серверный тип данных, то сервер может сообщить об ошибке, если не удается выполнить неявное преобразование к действительному серверному типу данных.  
  
## <a name="sspropinitdatatypecompatibility-behavior"></a>Поведение SSPROP_INIT_DATATYPECOMPATIBILITY  
 При SSPROP_INIT_DATATYPECOMPATIBILITY установлено в значение SSPROPVAL_DATATYPECOMPATIBILITY_SQL2000, типов новые даты и времени и связанные метаданные представляются клиентам как они отображаются для клиентов нижнего уровня, как описано в [изменения массового копирования для Улучшенные даты и времени типы &#40; OLE DB и ODBC &#41; ](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).  
  
## <a name="comparability-for-irowsetfind"></a>Сравнимость для IRowsetFind  
 Все операторы сравнения разрешены для новых типов данных даты-времени, так как они отображаются как строковые типы, а не типы даты-времени.  
  
## <a name="see-also"></a>См. также  
 [Дата и время усовершенствования &#40; OLE DB &#41;](../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
  

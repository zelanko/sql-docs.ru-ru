---
title: "Набор строк метаданные параметров и | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-ole-db-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: metadata [OLE DB]
ms.assetid: 31b318a4-20e7-4db0-b367-eb9938859029
caps.latest.revision: "32"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d45c0eafa873e0697c791d478eeffada7cfd91a0
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="metadata---parameter-and-rowset"></a>Метаданные - параметра и набор строк
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В этом разделе приведены сведения о следующем типе и элементах типа, связанных с усовершенствованиями даты и времени OLE DB.  
  
-   Структура DBBINDING  
  
-   **ICommandWithParameters::GetParameterInfo**  
  
-   **ICommandWithParameters::SetParameterInfo**  
  
-   **IColumnsRowset::GetColumnsRowset**  
  
-   **IColumnsInfo::GetColumnInfo**  
  
## <a name="icommandwithparametersgetparameterinfo"></a>ICommandWithParameters::GetParameterInfo  
 Следующие сведения возвращаются в структуре DBPARAMINFO через *prgParamInfo*:  
  
|Тип параметра|*wType*|*ulParamSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|-------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Clear|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Присвойте параметру|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19,21..27|0..7|Присвойте параметру|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26,28..34|0..7|Присвойте параметру|  
  
 Обратите внимание, что в некоторых случаях диапазоны значений не являются непрерывными. Это следствие добавления десятичной запятой, когда точность в долях секунды выше нуля.  
  
 Параметр DBPARAMFLAGS_SS_ISVARIABLESCALE допустим только при подключении к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) сервера. DBPARAMFLAGS_SS_ISVARIABLESCALE никогда не указывайте при соединении с серверами низкого уровня.  
  
## <a name="icommandwithparameterssetparameterinfo-and-implied-parameter-types"></a>Метод ICommandWithParameters::SetParameterInfo и неявные типы параметров  
 Сведения, предоставленные в структуре DBPARAMBINDINFO, должны соответствовать следующим требованиям.  
  
|*pwszDataSourceType*<br /><br /> (зависит от поставщика)|*pwszDataSourceType*<br /><br /> (OLE DB, обычный)|*ulParamSize*|*bScale*|  
|----------------------------------------------------|-------------------------------------------------|-------------------|--------------|  
||DBTYPE_DATE|6|Не учитывается|  
|date|DBTYPE_DBDATE|6|Не учитывается|  
||DBTYPE_DBTIME|10|Не учитывается|  
|time|DBTYPE_DBTIME2|10|0..7|  
|smalldatetime||16|Не учитывается|  
|datetime||16|Не учитывается|  
|datetime2 или DBTYPE_DBTIMESTAMP|DBTYPE_DBTIMESTAMP|16|0..7|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|0..7|  
  
 *BPrecision* параметр учитывается.  
  
 Значение «DBPARAMFLAGS_SS_ISVARIABLESCALE» не учитывается при отправке данных на сервер. Приложения могут принудительно использовать типы устаревших потока табличных данных (TDS), используя имена типа поставщика "**datetime**«и»**smalldatetime**». При подключении к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) серверов, "**datetime2**«будет использоваться формат и неявное преобразование сервера, при необходимости происходит, когда тип имеет имя»**datetime2**» или «DBTYPE_ DBTIMESTAMP». *bScale* учитывается, если имена типов, характерные для поставщика "**datetime**«или»**smalldatetime**" используются. В противном случае приложения должны убедиться, что *bScale* задано правильно. Приложения, обновленные с компонентами MDAC и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] от собственного клиента [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] , использующих «DBTYPE_DBTIMESTAMP» завершится ошибкой, если они не заданы *bScale* правильно. При соединении с экземплярами сервера более ранней, чем [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], *bScale* значение, отличное от 0 или 3 с именем «DBTYPE_DBTIMESTAMP» является ошибкой и будет возвращено E_FAIL.  
  
 Когда ICommandWithParameters::SetParameterInfo не вызывается, поставщик определяет сервер из тип тип привязки, как указано в IAccessor::CreateAccessor следующим образом:  
  
|Тип привязки|*pwszDataSourceType*<br /><br /> (зависит от поставщика)|  
|------------------|----------------------------------------------------|  
|DBTYPE_DATE|datetime2(0)|  
|DBTYPE_DBDATE|date|  
|DBTYPE_DBTIME|time(0)|  
|DBTYPE_DBTIME2|time(7)|  
|DBTYPE_DBTIMESTAMP|datetime2(7)|  
|DBTYPE_DBTIMESTAMPOFFSET|datetimeoffset(7)|  
  
## <a name="icolumnsrowsetgetcolumnsrowset"></a>IColumnsRowset::GetColumnsRowset  
 **IColumnsRowset::GetColumnsRowset** возвращает следующие столбцы:  
  
|Тип столбца|DBCOLUMN_TYPE|DBCOLUM_COLUMNSIZE|DBCOLUMN_PRECISION|DBCOLUMN_SCALE, DBCOLUMN_DATETIMEPRECISION|DBCOLUMN_FLAGS, DBCOLUMNFLAGS_SS_ISVARIABLESCALE|  
|-----------------|--------------------|-------------------------|-------------------------|--------------------------------------------------|---------------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Clear|  
|time|DBTYPE_DBTIME2|10|8, 10..16|0..7|Присвойте параметру|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Присвойте параметру|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Присвойте параметру|  
  
 В DBCOLUMN_FLAGS, DBCOLUMNFLAGS_ISFIXEDLENGTH всегда имеет значение TRUE для типов даты-времени, а следующие флаги всегда имеют значение FALSE.  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER  
  
-   DBCOLUMNFLAGS_MAYDEFER  
  
 Остальные флаги (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE и DBCOLUMNFLAGS_WRITEUNKNOWN) можно задать в зависимости от того, как определен столбец, а также от фактического запроса.  
  
 В DBCOLUMN_FLAGS новый флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE внедрен, чтобы приложения могли определять тип сервера столбцов, где DBCOLUMN_TYPE является DBTYPE_DBTIMESTAMP. Также должен использоваться флаг DBCOLUMN_SCALE или DBCOLUMN_DATETIMEPRECISION для указания типа сервера.  
  
 Флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE допустим только при подключении к [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (или более поздней версии) сервера. При соединении с серверами низкого уровня флаг DBCOLUMNFLAGS_SS_ISVARIABLESCALE остается неопределенным.  
  
## <a name="icolumnsinfogetcolumninfo"></a>IColumnsInfo::GetColumnInfo  
 Структура DBCOLUMNINFO возвращает следующие данные.  
  
|Тип параметра|*wType*|*ulColumnSize*|*bPrecision*|*bScale*|*dwFlags*<br /><br /> DBPARAMFLAGS_SS_ISVARIABLESCALE|  
|--------------------|-------------|--------------------|------------------|--------------|-----------------------------------------------------|  
|date|DBTYPE_DBDATE|6|10|0|Clear|  
|time(1..7)|DBTYPE_DBTIME2|10|8, 10..16|0..7|Присвойте параметру|  
|smalldatetime|DBTYPE_DBTIMESTAMP|16|16|0|Clear|  
|datetime|DBTYPE_DBTIMESTAMP|16|23|3|Clear|  
|datetime2|DBTYPE_DBTIMESTAMP|16|19, 21..27|0..7|Присвойте параметру|  
|datetimeoffset|DBTYPE_DBTIMESTAMPOFFSET|20|26, 28..34|0..7|Присвойте параметру|  
  
 В *dwFlags*, флаг DBCOLUMNFLAGS_ISFIXEDLENGTH всегда имеет значение true для типов даты и времени, а следующие флаги всегда имеют значение false:  
  
-   DBCOLUMNFLAGS_CACHEDEFERRED  
  
-   DBCOLUMNFLAGS_ISBOOKMARK  
  
-   DBCOLUMNFLAGS_ISCHAPTER  
  
-   DBCOLUMNFLAGS_ISLONG  
  
-   DBCOLUMNFLAGS_ISROWID  
  
-   DBCOLUMNFLAGS_ISROWVER, MAYDEFER  
  
 Остальные флаги (DBCOLUMNFLAGS_ISNULLABLE, DBCOLUMNFLAGS_MAYBENULL, DBCOLUMNFLAGS_WRITE и DBCOLUMNFLAGS_WRITEUNKNOWN) можно задавать.  
  
 Новый флаг dbcolumnflags_ss_isvariablescale внедрен в *dwFlags* чтобы приложения могли определять тип сервера столбцов, где *wType* является DBTYPE_DBTIMESTAMP. *bScale* также должен использоваться для определения типа сервера.  
  
## <a name="see-also"></a>См. также:  
 [Метаданные &#40; OLE DB &#41;](http://msdn.microsoft.com/library/605e3be5-aeea-4573-9847-b866ed3c8bff)  
  
  

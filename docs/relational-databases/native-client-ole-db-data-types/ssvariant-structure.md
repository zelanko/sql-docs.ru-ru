---
title: Структура SSVARIANT | Документация Майкрософт
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: cd20624744c9870cf5688c22af751d29d990a2db
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297028"
---
# <a name="ssvariant-structure"></a>Структура SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Структура **SSVARIANT,** которая определена в sqlncli.h, соответствует DBTYPE_SQLVARIANT [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] стоимости в поставщике NATIVE Client OLEDB.  
  
 **SSVARIANT** представляет собой избирательное соединение. В зависимости от значения элемента vt объект-получатель может определить, какой элемент следует считывать. Значения vt соответствуют типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, структура **SSVARIANT** может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB см. в статье об [индикаторах типа](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarks  
 Если DataTypeCompat==80, несколько подтипов **SSVARIANT** становятся строками. Например, следующие значения vt будут представлены в **SSVARIANT** в виде VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Если DateTypeCompat == 0, то эти типы будут представлены в собственном формате.  
  
 Для получения более подробной информации о SSPROP_INIT_DATATYPECOMPATIBILITY [см.](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
  
 Файл sqlncli.h содержит макросы доступа вариантов, которые упрощают дессылку типов элементов в структуре **SSVARIANT.** В качестве примера можно рассмотреть макрос V_SS_DATETIMEOFFSET, который можно использовать следующим образом:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Для полного набора макросов доступа для каждого члена структуры **SSVARIANT** обратитесь к файлу sqlncli.hi.  
  
 В приведенной ниже таблице описываются элементы структуры **SSVARIANT**.  
  
|Участник|Индикатор типа OLE DB|Тип данных OLE DB|Значение vt|Комментарии|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Указывает тип значения, которое содержится в структуре **SSVARIANT**.|  
|bTinyIntVa|DBTYPE_UI1|**Байт**|**VT_SS_UI1**|Поддерживает тип **данных tinyint.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|sShortIntVal|DBTYPE_I2|**Короткие**|**VT_SS_I2**|Поддерживает тип **данных smallint.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|lIntVal|DBTYPE_I4|**Длинные**|**VT_SS_I4**|Поддерживает тип данных **int.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Поддерживает тип данных **bigint.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|fltRealVal|DBTYPE_R4|**FLOAT**|**VT_SS_R4**|Поддерживает **реальный** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Поддерживает тип данных **поплавка.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает типы данных **money** и **smallmoney**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Поддерживает тип данных **бита.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|rgbGuidVal|DBTYPE_GUID|**Guid**|**VT_SS_GUID**|Поддерживает уникальный тип данных **идентификатора.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Поддерживает тип **численных** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Поддерживает тип данных **даты.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Поддерживает типы данных **smalldatetime**, **datetime** и **datetime2**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Поддерживает тип данных **времени.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) задает масштаб для значения *tTime2Val*.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Поддерживает тип данных **datetime2.** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<br /><br /> Содержит следующие элементы:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) задает масштаб для значения *tsDataTimeVal*.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Поддерживает тип[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] данных о времени **времени.**<br /><br /> Содержит следующие элементы:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) задает масштаб для значения *tsoDateTimeOffsetVal*.|  
|NCharVal|Отсутствует соответствующий индикатор типа OLE DB.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Поддерживает типы данных **nchar** и **nvarchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**SHORT**) задает фактическую длину строки, на которую указывает *pwchNCharVal*. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**SHORT**) задает максимальную длину строки, на которую указывает *pwchNCharVal*.<br /><br /> *pwchNCharVal* (**WCHAR** \*) — указатель на строку.<br /><br /> Неиспользуемые элементы: *rgbReserved*, *dwReserved* и *pwchReserved*.|  
|CharVal|Отсутствует соответствующий индикатор типа OLE DB.|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Поддерживает типы данных **char** и **varchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**SHORT**) задает фактическую длину строки, на которую указывает *pwchNCharVal*. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**SHORT**) задает максимальную длину строки, на которую указывает *pwchNCharVal*.<br /><br /> *pchCharVal* (**CHAR** \*) — указатель на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *rgbReserved*, *dwReserved* и *pwchReserved*.|  
|BinaryVal|Отсутствует соответствующий индикатор типа OLE DB.|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Поддерживает типы данных **binary** и **varbinary**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**SHORT**) задает фактическую длину для данных, на которую указывает *pwchNCharVal*.<br /><br /> *sMaxLength* (**SHORT**) задает максимальную длину для данных, на которые указывает *pwchNCharVal*.<br /><br /> *prgbBinaryVal* (**BYTE** \*) — указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *dwReserved*.|  
|UnknownType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (OLE DB)](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

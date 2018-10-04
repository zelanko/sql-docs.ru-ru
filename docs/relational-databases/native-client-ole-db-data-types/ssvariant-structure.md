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
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 64f71a290e9a3f56249c3564ed9d7eefdc9a76a2
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47654812"
---
# <a name="ssvariant-structure"></a>Структура SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  **SSVARIANT** структура, которая определена в файле sqlncli.h, соответствует значению DBTYPE_SQLVARIANT в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщика OLEDB для собственного клиента.  
  
 **SSVARIANT** представляет собой Избирательное. В зависимости от значения элемента vt объект-получатель может определить, какой элемент следует считывать. Значения vt соответствуют типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, структура **SSVARIANT** может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB, см. в разделе [индикаторов типа](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Примечания  
 Если DataTypeCompat==80, несколько подтипов **SSVARIANT** становятся строками. Например, следующие значения vt будут представлены в **SSVARIANT** в виде VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Если DateTypeCompat == 0, то эти типы будут представлены в собственном формате.  
  
 Дополнительные сведения о SSPROP_INIT_DATATYPECOMPATIBILITY см. в разделе [Using Connection String Keywords with SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Файл sqlncli.h содержит макросы variant доступа, которые упрощают разыменование типов, входящих в **SSVARIANT** структуры. В качестве примера можно рассмотреть макрос V_SS_DATETIMEOFFSET, который можно использовать следующим образом:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Полный набор макросов доступа для каждого члена **SSVARIANT** структуры см. в файле sqlncli.hi.  
  
 В приведенной ниже таблице описываются элементы структуры **SSVARIANT**.  
  
|Член|Индикатор типа OLE DB|Тип данных OLE DB|Значение vt|Комментарии|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Указывает тип значения, которое содержится в структуре **SSVARIANT**.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Поддерживает **tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|Поддерживает **smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Поддерживает **int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Поддерживает **bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Поддерживает **реальных** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Поддерживает **float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает **деньги** и **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Поддерживает **бит** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Поддерживает **uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Поддерживает **числовых** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Поддерживает тип данных **date**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Поддерживает **smalldatetime**, **datetime**, и **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Поддерживает **время** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tTime2Val* значение.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Поддерживает **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tsDataTimeVal* значение.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Поддерживает **datetimeoffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tsoDateTimeOffsetVal* значение.|  
|NCharVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Поддерживает **nchar** и **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину для строки, на которую *pwchNCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину для строки, на которую *pwchNCharVal* точек.<br /><br /> *pwchNCharVal* (**WCHAR** \*) указатель на строку.<br /><br /> Неиспользуемые элементы: *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|CharVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Поддерживает **char** и **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину строки, на которую *pchCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину для строки, на которую *pchCharVal* точек.<br /><br /> *pchCharVal* (**CHAR** \*) указатель на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|BinaryVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Поддерживает **двоичных** и **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину данных, на которые *prgbBinaryVal* точек.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину данных, на которые *prgbBinaryVal* точек.<br /><br /> *prgbBinaryVal* (**БАЙТОВ** \*) указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *dwReserved*.|  
|UnknownType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также  
 [Типы данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

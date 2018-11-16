---
title: Структура SSVARIANT | Документация Майкрософт
description: Структура SSVARIANT в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: d500dc56ff128029ebba1576a84919f9694d8903
ms.sourcegitcommit: 63b4f62c13ccdc2c097570fe8ed07263b4dc4df0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 11/13/2018
ms.locfileid: "51602234"
---
# <a name="ssvariant-structure"></a>Структура SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **SSVARIANT** структуру, которая определена в msoledbsql.h, соответствует значению DBTYPE_SQLVARIANT в драйвере OLE DB для SQL Server.  
  
 **SSVARIANT** представляет собой Избирательное. В зависимости от значения элемента vt объект-получатель может определить, какой элемент следует считывать. Значения vt соответствуют типам данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Таким образом, структура **SSVARIANT** может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB, см. в разделе [индикаторов типа](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarks  
 Если DataTypeCompat==80, несколько подтипов **SSVARIANT** становятся строками. Например, следующие значения vt будут представлены в **SSVARIANT** в виде VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Если DateTypeCompat == 0, то эти типы будут представлены в собственном формате.  
  
 Дополнительные сведения о SSPROP_INIT_DATATYPECOMPATIBILITY см. в разделе [с помощью ключевых слов строки подключения с драйвер OLE DB для SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Файл msoledbsql.h содержит макросы для доступа к значениям variant, которые упрощают разыменование типов, входящих в структуру **SSVARIANT**. В качестве примера можно рассмотреть макрос V_SS_DATETIMEOFFSET, который можно использовать следующим образом:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Полный набор макросов доступа для каждого члена **SSVARIANT** структуры, ознакомьтесь с файлом msoledbsql.h.  
  
 В приведенной ниже таблице описываются элементы структуры **SSVARIANT**.  
  
|Член|Индикатор типа OLE DB|Тип данных OLE DB|Значение vt|Комментарии|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Указывает тип значения, которое содержится в структуре **SSVARIANT**.|  
|bTinyIntVal|DBTYPE_UI1|**BYTE**|**VT_SS_UI1**|Поддерживает **tinyint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|sShortIntVal|DBTYPE_I2|**SHORT**|**VT_SS_I2**|Поддерживает **smallint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Поддерживает **int** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Поддерживает **bigint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Поддерживает **реальных** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Поддерживает **float** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает **деньги** и **smallmoney** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Поддерживает **бит** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Поддерживает **uniqueidentifier** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Поддерживает **числовых** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Поддерживает тип данных **date**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Поддерживает **smalldatetime**, **datetime**, и **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Поддерживает **время** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tTime2Val* значение.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Поддерживает **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tsDataTimeVal* значение.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Поддерживает **datetimeoffset** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tsoDateTimeOffsetVal* значение.|  
|NCharVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Поддерживает **nchar** и **nvarchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину строки, на которую *pwchNCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину для строки, на которую *pwchNCharVal* точек.<br /><br /> *pwchNCharVal* (**WCHAR** \*) указатель на строку.<br /><br /> Неиспользуемые элементы: *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|CharVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Поддерживает **char** и **varchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину строки, на которую *pchCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину для строки, на которую *pchCharVal* точек.<br /><br /> *pchCharVal* (**CHAR** \*) указатель на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|BinaryVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Поддерживает **двоичных** и **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину данных, на которые *prgbBinaryVal* точек.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину данных, на которые *prgbBinaryVal* точек.<br /><br /> *prgbBinaryVal* (**БАЙТОВ** \*) указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *dwReserved*.|  
|UnknownType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  

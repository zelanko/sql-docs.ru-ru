---
title: Структура SSVARIANT | Документы Microsoft
description: Структура SSVARIANT в драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|ole-db-data-types
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 9afd7d6ce87ac49c060347287d4b7a081ea5bb41
ms.sourcegitcommit: e1bc8c486680e6d6929c0f5885d97d013a537149
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2018
ms.locfileid: "35666384"
---
# <a name="ssvariant-structure"></a>Структура SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **SSVARIANT** структуру, которая определена в msoledbsql.h, соответствует значению DBTYPE_SQLVARIANT в драйвер OLE DB для SQL Server.  
  
 **SSVARIANT** представляет собой Избирательное соединение. В зависимости от значения элемента vt потребитель может определить, какой элемент следует считывать. значения VT соответствуют [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных. Таким образом **SSVARIANT** структуру может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB см. в разделе [индикаторов типа](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Примечания  
 Если DataTypeCompat == 80, несколько **SSVARIANT** подтипы становятся строками. Например, следующие значения vt будут отображаться в **SSVARIANT** виде VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Если DateTypeCompat == 0, то эти типы будут представлены в собственном формате.  
  
 Дополнительные сведения о SSPROP_INIT_DATATYPECOMPATIBILITY см. в разделе [с помощью ключевых слов строки подключения с драйвер OLE DB для SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md).  
  
 Файл msoledbsql.h содержит макросы variant доступа, которые упрощают разыменование типов, входящих в **SSVARIANT** структуры. В качестве примера можно рассмотреть макрос V_SS_DATETIMEOFFSET, который можно использовать следующим образом:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Полный набор макросов доступа для каждого члена **SSVARIANT** структуры, ознакомьтесь с файлом msoledbsql.h.  
  
 В следующей таблице описаны элементы **SSVARIANT** структуры:  
  
|Член|Индикатор типа OLE DB|Тип данных OLE DB|Значение vt|Комментарии|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Указывает тип значения, содержащегося в **SSVARIANT** структуры.|  
|bTinyIntVal|DBTYPE_UI1|**БАЙТ**|**VT_SS_UI1**|Поддерживает **tinyint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|sShortIntVal|DBTYPE_I2|**КОРОТКИЙ**|**VT_SS_I2**|Поддерживает **smallint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|lIntVal|DBTYPE_I4|**LONG**|**VT_SS_I4**|Поддерживает **int** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Поддерживает **bigint** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Поддерживает **реальные** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Поддерживает **float** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает **money** и **smallmoney** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Поддерживает **бит** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Поддерживает **uniqueidentifier** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Поддерживает **числовое** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Поддерживает **даты** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Поддерживает **smalldatetime**, **datetime**, и **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Поддерживает **время** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tTime2Val* значение.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Поддерживает **datetime2** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tsDataTimeVal* значение.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Поддерживает **datetimeoffset** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**БАЙТОВ**) Задает масштаб для *tsoDateTimeOffsetVal* значение.|  
|NCharVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Поддерживает **nchar** и **nvarchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину строки, на которой *pwchNCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину строки, на которой *pwchNCharVal* точек.<br /><br /> *pwchNCharVal* (**WCHAR** \*) указатель на строку.<br /><br /> Неиспользуемые элементы: *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|CharVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Поддерживает **char** и **varchar** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину строки, на которой *pchCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину строки, на которой *pchCharVal* точек.<br /><br /> *pchCharVal* (**CHAR** \*) указатель на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|BinaryVal|Отсутствует соответствующий индикатор типа OLE DB.|**Структура _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Поддерживает **двоичных** и **varbinary** [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**КОРОТКИЕ**) указывает фактическую длину данных, к которому *prgbBinaryVal* точек.<br /><br /> *sMaxLength* (**КОРОТКИЕ**) указывает максимальную длину данных, к которому *prgbBinaryVal* точек.<br /><br /> *prgbBinaryVal* (**БАЙТОВ** \*) указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *dwReserved*.|  
|UnknownType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также  
 [Типы данных &#40;OLE DB&#41;](../../oledb/ole-db-data-types/data-types-ole-db.md)  
  
  

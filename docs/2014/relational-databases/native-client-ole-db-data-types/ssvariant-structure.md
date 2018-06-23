---
title: Структура SSVARIANT | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- SSVARIANT
helpviewer_keywords:
- SSVARIANT struct
ms.assetid: d13c6aa6-bd49-467a-9093-495df8f1e2d9
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 8c8d98a54155179fe481fc0a7202a07e6cbf2aff
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36189309"
---
# <a name="ssvariant-structure"></a>Структура SSVARIANT
  Структура `SSVARIANT`, определяемая в файле sqlncli.h, соответствует значению DBTYPE_SQLVARIANT в поставщике OLEDB для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 `SSVARIANT` представляет собой избирательное соединение. В зависимости от значения элемента vt потребитель может определить, какой элемент следует считывать. значения VT соответствуют [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных. Таким образом, структура `SSVARIANT` может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB см. в разделе [индикаторов типа](http://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Примечания  
 Если DataTypeCompat==80, несколько подтипов `SSVARIANT` становятся строками. Например, следующие значения vt будут представлены в `SSVARIANT` в виде VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Если DateTypeCompat == 0, то эти типы будут представлены в собственном формате.  
  
 Дополнительные сведения о SSPROP_INIT_DATATYPECOMPATIBILITY см. в разделе [с помощью ключевых слов строки подключения с собственным клиентом SQL Server](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Файл sqlncli.h содержит макросы для доступа к значениям variant, которые упрощают разыменование типов, входящих в структуру `SSVARIANT`. В качестве примера можно рассмотреть макрос V_SS_DATETIMEOFFSET, который можно использовать следующим образом:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Полный набор макросов доступа для каждого элемента структуры `SSVARIANT` см. в файле sqlncli.hi.  
  
 Следующая таблица описывает элементы структуры `SSVARIANT`.  
  
|Член|Индикатор типа OLE DB|Тип данных OLE DB|Значение vt|Комментарии|  
|------------|---------------------------|------------------------|--------------|--------------|  
|VT|SSVARTYPE|||Указывает тип значения, которое содержится в структуре `SSVARIANT`.|  
|bTinyIntVal|DBTYPE_UI1|`BYTE`|`VT_SS_UI1`|Поддерживает `tinyint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|sShortIntVal|DBTYPE_I2|`SHORT`|`VT_SS_I2`|Поддерживает `smallint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|lIntVal|DBTYPE_I4|`LONG`|`VT_SS_I4`|Поддерживает `int` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|llBigIntVal|DBTYPE_I8|`LARGE_INTEGER`|`VT_SS_I8`|Поддерживает `bigint` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|fltRealVal|DBTYPE_R4|`float`|`VT_SS_R4`|Поддерживает `real` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dblFloatVal|DBTYPE_R8|`double`|`VT_SS_R8`|Поддерживает `float` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|cyMoneyVal|DBTYPE_CY|`LARGE_INTEGER`|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает `money` и **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.|  
|fBitVal|DBTYPE_BOOL|`VARIANT_BOOL`|`VT_SS_BIT`|Поддерживает `bit` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|rgbGuidVal|DBTYPE_GUID|`GUID`|`VT_SS_GUID`|Поддерживает `uniqueidentifier` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|numNumericVal|DBTYPE_NUMERIC|`DB_NUMERIC`|`VT_SS_NUMERIC`|Поддерживает `numeric` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dDateVal|DBTYPE_DATE|`DBDATE`|`VT_SS_DATE`|Поддерживает `date` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2`|Поддерживает `smalldatetime`, `datetime`, и `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.|  
|Time2Val|DBTYPE_DBTIME2|`DBTIME2`|`VT_SS_TIME2`|Поддерживает `time` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* (`DBTIME2`)<br /><br /> *bScale* (`BYTE`) Задает масштаб для *tTime2Val* значение.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|`DBTIMESTAMP`|`VT_SS_DATETIME2`|Поддерживает `datetime2` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (`BYTE`) Задает масштаб для *tsDataTimeVal* значение.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|`DBTIMESTAMPOFFSET`|`VT_SS_DATETIMEOFFSET`|Поддерживает `datetimeoffset` [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.<br /><br /> Содержит следующие элементы:<br /><br /> *tsoDateTimeOffsetVal* (`DBTIMESTAMPOFFSET`)<br /><br /> *bScale* (`BYTE`) Задает масштаб для *tsoDateTimeOffsetVal* значение.|  
|NCharVal|Отсутствует соответствующий индикатор типа OLE DB.|`struct _NCharVal`|`VT_SS_WVARSTRING,`<br /><br /> `VT_SS_WSTRING`|Поддерживает `nchar` и **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (`SHORT`) указывает фактическую длину строки, на которой *pwchNCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (`SHORT`) указывает максимальную длину строки, на которой *pwchNCharVal* точек.<br /><br /> *pwchNCharVal* (`WCHAR` \*) указатель на строку.<br /><br /> Неиспользуемые элементы: *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|CharVal|Отсутствует соответствующий индикатор типа OLE DB.|`struct _CharVal`|`VT_SS_STRING,`<br /><br /> `VT_SS_VARSTRING`|Поддерживает `char` и **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (`SHORT`) указывает фактическую длину строки, на которой *pchCharVal* точек. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (`SHORT`) указывает максимальную длину строки, на которой *pchCharVal* точек.<br /><br /> *pchCharVal* (`CHAR` \*) указатель на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *rgbReserved*, *dwReserved*, и *pwchReserved*.|  
|BinaryVal|Отсутствует соответствующий индикатор типа OLE DB.|`struct _BinaryVal`|`VT_SS_VARBINARY,`<br /><br /> `VT_SS_BINARY`|Поддерживает `binary` и **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных.<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (`SHORT`) указывает фактическую длину данных, к которому *prgbBinaryVal* точек.<br /><br /> *sMaxLength* (`SHORT`) указывает максимальную длину данных, к которому *prgbBinaryVal* точек.<br /><br /> *prgbBinaryVal* (`BYTE` \*) указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *dwReserved*.|  
|UnknownType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также  
 [Типы данных &#40;OLE DB&#41;](data-types-ole-db.md)  
  
  
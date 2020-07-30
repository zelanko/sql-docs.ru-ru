---
title: Структура SSVARIANT (поставщик собственного клиента OLE DB)
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
ms.openlocfilehash: ddd98b45cf44f840dfc236f8a0a1b5d809db7288
ms.sourcegitcommit: 75f767c7b1ead31f33a870fddab6bef52f99906b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87331983"
---
# <a name="ssvariant-structure-in-sql-server-native-client"></a>Структура SSVARIANT в SQL Server Native Client
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

  Структура **SSVARIANT** , определенная в sqlncli. h, соответствует значению DBTYPE_SQLVARIANT в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поставщике OLEDB собственного клиента.  
  
 **SSVARIANT** представляет собой избирательное соединение. В зависимости от значения элемента vt объект-получатель может определить, какой элемент следует считывать. Значения vt соответствуют типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, структура **SSVARIANT** может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB см. в статье об [индикаторах типа](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
## <a name="remarks"></a>Remarks  
 Если DataTypeCompat==80, несколько подтипов **SSVARIANT** становятся строками. Например, следующие значения vt будут представлены в **SSVARIANT** в виде VT_SS_WVARSTRING:  
  
-   VT_SS_DATETIMEOFFSET  
  
-   VT_SS_DATETIME2  
  
-   VT_SS_TIME2  
  
-   VT_SS_DATE  
  
 Если DateTypeCompat == 0, то эти типы будут представлены в собственном формате.  
  
 Дополнительные сведения о SSPROP_INIT_DATATYPECOMPATIBILITY см. в разделе [Использование ключевых слов строки подключения с SQL Server Native Client](../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).  
  
 Файл sqlncli. h содержит макросы с вариантами доступа, упрощающие разыменование типов элементов в структуре **SSVARIANT** . В качестве примера можно рассмотреть макрос V_SS_DATETIMEOFFSET, который можно использовать следующим образом:  
  
```  
memcpy(&V_SS_DATETIMEOFFSET(pssVar).tsoDateTimeOffsetVal, pDTO, cbNative);  
V_SS_DATETIMEOFFSET(pssVar).bScale = bScale;  
```  
  
 Полный набор макросов доступа для каждого элемента структуры **SSVARIANT** см. в файле sqlncli. Hi.  
  
 В приведенной ниже таблице описываются элементы структуры **SSVARIANT**.  
  
|Участник|Индикатор типа OLE DB|Тип данных OLE DB|Значение vt|Комментарии|  
|------------|---------------------------|------------------------|--------------|--------------|  
|vt|SSVARTYPE|||Указывает тип значения, которое содержится в структуре **SSVARIANT**.|  
|bTinyIntVa|DBTYPE_UI1|**ДВУХБАЙТОВЫХ**|**VT_SS_UI1**|Поддерживает **tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных tinyint.|  
|sShortIntVal|DBTYPE_I2|**ПРОМЕЖУТОК**|**VT_SS_I2**|Поддерживает **smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных smallint.|  
|lIntVal|DBTYPE_I4|**ПОДДЕРЖИВАЕМ**|**VT_SS_I4**|Поддерживает **int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных int.|  
|llBigIntVal|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Поддерживает **bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных bigint.|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Поддерживает **реальный** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Поддерживает **float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных float.|  
|cyMoneyVal|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает типы данных **money** и **smallmoney**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|fBitVal|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Поддерживает **bit** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных bit.|  
|rgbGuidVal|DBTYPE_GUID|**GUID**|**VT_SS_GUID**|Поддерживает **uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных uniqueidentifier.|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Поддерживает **числовой** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dDateVal|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Поддерживает **date** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных Date.|  
|tsDateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Поддерживает типы данных **smalldatetime**, **datetime** и **datetime2**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Поддерживает **time** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных time.<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**BYTE**) задает масштаб для значения *tTime2Val*.|  
|DateTimeVal|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Поддерживает **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных datetime2.<br /><br /> Содержит следующие элементы:<br /><br /> *tsDataTimeVal* (DBTIMESTAMP)<br /><br /> *bScale* (**BYTE**) задает масштаб для значения *tsDataTimeVal*.|  
|DateTimeOffsetVal|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Поддерживает **datetimeoffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных DateTimeOffset.<br /><br /> Содержит следующие элементы:<br /><br /> *tsoDateTimeOffsetVal* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**BYTE**) задает масштаб для значения *tsoDateTimeOffsetVal*.|  
|NCharVal|Отсутствует соответствующий индикатор типа OLE DB.|**struct _NCharVal**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Поддерживает типы данных **nchar** и **nvarchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**SHORT**) задает фактическую длину строки, на которую указывает *pwchNCharVal*. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**SHORT**) задает максимальную длину строки, на которую указывает *pwchNCharVal*.<br /><br /> *pwchNCharVal* (**WCHAR** \*) — указатель на строку.<br /><br /> Неиспользуемые элементы: *rgbReserved*, *dwReserved* и *pwchReserved*.|  
|CharVal|Отсутствует соответствующий индикатор типа OLE DB.|**struct _CharVal**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Поддерживает типы данных **char** и **varchar**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**SHORT**) задает фактическую длину строки, на которую указывает *pwchNCharVal*. Не содержит завершающего нуля.<br /><br /> *sMaxLength* (**SHORT**) задает максимальную длину строки, на которую указывает *pwchNCharVal*.<br /><br /> *pchCharVal* (**CHAR** \*) — указатель на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *rgbReserved*, *dwReserved* и *pwchReserved*.|  
|BinaryVal|Отсутствует соответствующий индикатор типа OLE DB.|**struct _BinaryVal**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Поддерживает типы данных **binary** и **varbinary**[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].<br /><br /> Содержит следующие элементы:<br /><br /> *sActualLength* (**SHORT**) задает фактическую длину для данных, на которую указывает *pwchNCharVal*.<br /><br /> *sMaxLength* (**SHORT**) задает максимальную длину для данных, на которые указывает *pwchNCharVal*.<br /><br /> *prgbBinaryVal* (**BYTE** \*) — указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *dwReserved*.|  
|UnknownType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных (OLE DB)](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

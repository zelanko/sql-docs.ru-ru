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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 2298bbbfcdb4c0245d9b932152c21f39d7e884f0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73770743"
---
# <a name="ssvariant-structure"></a>Структура SSVARIANT
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Структура **SSVARIANT** , определенная в sqlncli. h, соответствует значению DBTYPE_SQLVARIANT в поставщике OLEDB [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента.  
  
 **SSVARIANT** — это отличительное объединение. В зависимости от значения элемента vt объект-получатель может определить, какой элемент следует считывать. Значения vt соответствуют типам данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Таким образом, структура **SSVARIANT** может содержать любой тип SQL Server. Дополнительные сведения о структуре данных для стандартных типов OLE DB см. в разделе [индикаторы типов](https://go.microsoft.com/fwlink/?LinkId=122171).  
  
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
|VT|SSVARTYPE|||Указывает тип значения, которое содержится в структуре **SSVARIANT**.|  
|бтининтвал|DBTYPE_UI1|**ДВУХБАЙТОВЫХ**|**VT_SS_UI1**|Поддерживает тип данных **tinyint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|сшортинтвал|DBTYPE_I2|**ПРОМЕЖУТОК**|**VT_SS_I2**|Поддерживает тип данных **smallint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|линтвал|DBTYPE_I4|**ПОДДЕРЖИВАЕМ**|**VT_SS_I4**|Поддерживает тип данных **int** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|ллбигинтвал|DBTYPE_I8|**LARGE_INTEGER**|**VT_SS_I8**|Поддерживает тип данных **bigint** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|fltRealVal|DBTYPE_R4|**float**|**VT_SS_R4**|Поддерживает **реальный** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|dblFloatVal|DBTYPE_R8|**double**|**VT_SS_R8**|Поддерживает тип данных **float** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|цимонэйвал|DBTYPE_CY|**LARGE_INTEGER**|**VT_SS_MONEY VT_SS_SMALLMONEY**|Поддерживает типы данных **money** и **smallmoney** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|фбитвал|DBTYPE_BOOL|**VARIANT_BOOL**|**VT_SS_BIT**|Поддерживает тип данных **bit** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|rgbGuidVal|DBTYPE_GUID|**УСТРОЙСТВА**|**VT_SS_GUID**|Поддерживает тип данных **uniqueidentifier** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|numNumericVal|DBTYPE_NUMERIC|**DB_NUMERIC**|**VT_SS_NUMERIC**|Поддерживает **числовой** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] тип данных.|  
|ддатевал|DBTYPE_DATE|**DBDATE**|**VT_SS_DATE**|Поддерживает тип данных **Date** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|тсдатетимевал|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_SMALLDATETIME VT_SS_DATETIME VT_SS_DATETIME2**|Поддерживает типы данных **smalldatetime**, **DateTime**и **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .|  
|Time2Val|DBTYPE_DBTIME2|**DBTIME2**|**VT_SS_TIME2**|Поддерживает тип данных **time** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *tTime2Val* (**DBTIME2**)<br /><br /> *bScale* (**Byte**) задает масштаб для значения *tTime2Val* .|  
|датетимевал|DBTYPE_DBTIMESTAMP|**DBTIMESTAMP**|**VT_SS_DATETIME2**|Поддерживает тип данных **datetime2** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *тсдататимевал* (DBTIMESTAMP)<br /><br /> *bScale* (**Byte**) задает масштаб для значения *тсдататимевал* .|  
|датетимеоффсетвал|DBTYPE_DBTIMESTAMPOFSET|**DBTIMESTAMPOFFSET**|**VT_SS_DATETIMEOFFSET**|Поддерживает тип данных **DateTimeOffset** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *тсодатетимеоффсетвал* (**DBTIMESTAMPOFFSET**)<br /><br /> *bScale* (**Byte**) задает масштаб для значения *тсодатетимеоффсетвал* .|  
|нчарвал|Отсутствует соответствующий индикатор типа OLE DB.|**_NCharVal структуры**|**VT_SS_WVARSTRING,**<br /><br /> **VT_SS_WSTRING**|Поддерживает типы данных **nchar** и **nvarchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *сактуалленгс* (**Short**) задает фактическую длину строки, в которую *пвчнчарвал* указывает. Не содержит завершающего нуля.<br /><br /> *смаксленгс* (**Short**) задает максимальную длину строки, на которую указывает *пвчнчарвал* .<br /><br /> *пвчнчарвал* (**WCHAR** \*) указатель на строку.<br /><br /> Неиспользуемые элементы: *ргбресервед*, *двресервед*и *пвчресервед*.|  
|чарвал|Отсутствует соответствующий индикатор типа OLE DB.|**_CharVal структуры**|**VT_SS_STRING,**<br /><br /> **VT_SS_VARSTRING**|Поддерживает типы данных **char** и **varchar** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *сактуалленгс* (**Short**) задает фактическую длину строки, в которую *пччарвал* указывает. Не содержит завершающего нуля.<br /><br /> *смаксленгс* (**Short**) задает максимальную длину строки, на которую указывает *пччарвал* .<br /><br /> *пччарвал* (**char** \*) указатель на строку.<br /><br /> Неиспользуемые элементы:<br /><br /> *ргбресервед*, *двресервед*и *пвчресервед*.|  
|бинаривал|Отсутствует соответствующий индикатор типа OLE DB.|**_BinaryVal структуры**|**VT_SS_VARBINARY,**<br /><br /> **VT_SS_BINARY**|Поддерживает типы данных **binary** и **varbinary** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .<br /><br /> Содержит следующие элементы:<br /><br /> *сактуалленгс* (**Short**) задает фактическую длину данных, на которые указывает *пргббинаривал* .<br /><br /> *смаксленгс* (**Short**) задает максимальную длину данных, на которые указывает *пргббинаривал* .<br /><br /> *пргббинаривал* (**Byte** \*) указатель на двоичные данные.<br /><br /> Неиспользуемый элемент: *двресервед*.|  
|ункновнтипе|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
|BLOBType|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|НЕ ИСПОЛЬЗУЕТСЯ|  
  
## <a name="see-also"></a>См. также:  
 [Типы данных &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
  

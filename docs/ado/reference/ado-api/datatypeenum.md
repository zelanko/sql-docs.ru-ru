---
title: DataTypeEnum | Документация Майкрософт
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataTypeEnum
helpviewer_keywords:
- DataTypeEnum enumeration [ADO]
ms.assetid: 2c57eca6-9336-4b06-ba10-9fef5926b1d0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7cb3e56d0219973be97b694ee2b22dbbb58eb0d8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698526"
---
# <a name="datatypeenum"></a>DataTypeEnum
Указывает тип данных [поле](../../../ado/reference/ado-api/field-object.md), [параметр](../../../ado/reference/ado-api/parameter-object.md), или [свойство](../../../ado/reference/ado-api/property-object-ado.md). В круглых скобках в столбце "Описание" в следующей таблице показан соответствующий индикатор типа OLE DB.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**AdArray**|0x2000|Значение флага всегда в сочетании с другой константой типа данных, который указывает массив другого типа данных. Не применяется к ADOX.|  
|**adBigInt**|20|Указывает, 8 байтовое целое число со знаком (DBTYPE_I8).|  
|**adBinary**|128|Указывает, двоичное значение (DBTYPE_BYTES).|  
|**adBoolean**|11|Указывает **логическое** значение (DBTYPE_BOOL).|  
|**adBSTR**|8|Указывает строку символов с завершающим нулем (Юникод) (DBTYPE_BSTR).|  
|**adChapter**|136|Указывает значение Глава 4 байта, определяет строки в набор дочерних строк (DBTYPE_HCHAPTER).|  
|**adChar**|129|Указывает строковое значение (DBTYPE_STR).|  
|**adCurrency**|6|Указывает значение валюты (DBTYPE_CY). Валюта — это число с фиксированной запятой с четырьмя цифрами справа от десятичной запятой. Он хранится в 8 байтовое целое число со знаком с шагом в 10 000.|  
|**adDate**|7|Показывает значение date (DBTYPE_DATE). Дата сохраняется как значение типа double, целая часть из которых является количество дней, прошедшему с 30 декабря 1899, а дробная часть которого равна части дня.|  
|**adDBDate**|133|Показывает значение date (ГГГГММДД) (DBTYPE_DBDATE).|  
|**adDBTime**|134|Указывает значение времени (ЧЧММСС) (DBTYPE_DBTIME).|  
|**adDBTimeStamp**|135|Указывает отметку даты и времени (ггггммддччммсс плюс дроби миллиардных) (DBTYPE_DBTIMESTAMP).|  
|**adDecimal**|14|Указывает точное числовое значение с фиксированной точностью и масштабом (DBTYPE_DECIMAL).|  
|**adDouble**|5|Указывает значение с плавающей запятой двойной точности (DBTYPE_R8).|  
|**adEmpty**|0|Не заданы значения (DBTYPE_EMPTY).|  
|**adError**|10|Указывает 32-разрядный код ошибки (DBTYPE_ERROR).|  
|**adFileTime**|64|Показывает 64-разрядное значение, представляющее количество 100-наносекундных интервалов с 1 января 1601 г. (DBTYPE_FILETIME).|  
|**adGUID**|72|Глобально уникальный идентификатор (GUID) (DBTYPE_GUID).|  
|**adIDispatch**|9|Указывает указатель на **IDispatch** интерфейс COM-объекта (DBTYPE_IDISPATCH).<br /><br /> **Примечание** этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adInteger**|3|Указывает четырехбайтовое целое число со знаком (DBTYPE_I4).|  
|**adIUnknown**|13|Указывает указатель на **IUnknown** интерфейс COM-объекта (DBTYPE_IUNKNOWN).<br /><br /> **Примечание** этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adLongVarBinary**|205|Указывает Длинное двоичное значение.|  
|**adLongVarChar**|201|Указывает длинное строковое значение.|  
|**adLongVarWChar**|203|Указывает значение долго нулем строку Юникода.|  
|**adNumeric**|131|Указывает точное числовое значение с фиксированной точностью и масштабом (DBTYPE_NUMERIC).|  
|**adPropVariant**|138|Указывает автоматизации (DBTYPE_PROP_VARIANT) PROPVARIANT.|  
|**adSingle**|4|Указывает значение с плавающей запятой одиночной точности (DBTYPE_R4).|  
|**adSmallInt**|2|Указывает двухбайтное целое число со знаком (DBTYPE_I2).|  
|**adTinyInt**|16|Указывает однобайтовое целое число со знаком (DBTYPE_I1).|  
|**adUnsignedBigInt**|21|Указывает, 8 байтовое целое число без знака (DBTYPE_UI8).|  
|**adUnsignedInt**|19|Указывает целое число без знака размером 4 байта (DBTYPE_UI4).|  
|**adUnsignedSmallInt**|18|Указывает целое число без знака размером 2 байта (DBTYPE_UI2).|  
|**adUnsignedTinyInt**|17|Указывает однобайтовое целое число без знака (DBTYPE_UI1).|  
|**adUserDefined**|132|Указывает пользовательскую переменную (DBTYPE_UDT).|  
|**adVarBinary**|204|Указывает, двоичное значение.|  
|**adVarChar**|200|Указывает строковое значение.|  
|**adVariant**|12|Указывает автоматизации **Variant** (DBTYPE_VARIANT).<br /><br /> **Примечание** этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adVarNumeric**|139|Указывает числовое значение.|  
|**adVarWChar**|202|Указывает, заканчивающуюся нулем строку символов Юникода.|  
|**adWChar**|130|Указывает строку символов Юникода (DBTYPE_WSTR) нулем.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO и WFC  
 Пакет: **com.ms.wfc.data**  
  
|Константа|  
|--------------|  
|AdoEnums.DataType.ARRAY|  
|AdoEnums.DataType.BIGINT|  
|AdoEnums.DataType.BINARY|  
|AdoEnums.DataType.BOOLEAN|  
|AdoEnums.DataType.BSTR|  
|AdoEnums.DataType.CHAPTER|  
|AdoEnums.DataType.CHAR|  
|AdoEnums.DataType.CURRENCY|  
|AdoEnums.DataType.DATE|  
|AdoEnums.DataType.DBDATE|  
|AdoEnums.DataType.DBTIME|  
|AdoEnums.DataType.DBTIMESTAMP|  
|AdoEnums.DataType.DECIMAL|  
|AdoEnums.DataType.DOUBLE|  
|AdoEnums.DataType.EMPTY|  
|AdoEnums.DataType.ERROR|  
|AdoEnums.DataType.FILETIME|  
|AdoEnums.DataType.GUID|  
|AdoEnums.DataType.IDISPATCH|  
|AdoEnums.DataType.INTEGER|  
|AdoEnums.DataType.IUNKNOWN|  
|AdoEnums.DataType.LONGVARBINARY|  
|AdoEnums.DataType.LONGVARCHAR|  
|AdoEnums.DataType.LONGVARWCHAR|  
|AdoEnums.DataType.NUMERIC|  
|AdoEnums.DataType.PROPVARIANT|  
|AdoEnums.DataType.SINGLE|  
|AdoEnums.DataType.SMALLINT|  
|AdoEnums.DataType.TINYINT|  
|AdoEnums.DataType.UNSIGNEDBIGINT|  
|AdoEnums.DataType.UNSIGNEDINT|  
|AdoEnums.DataType.UNSIGNEDSMALLINT|  
|AdoEnums.DataType.UNSIGNEDTINYINT|  
|AdoEnums.DataType.USERDEFINED|  
|AdoEnums.DataType.VARBINARY|  
|AdoEnums.DataType.VARCHAR|  
|AdoEnums.DataType.VARIANT|  
|AdoEnums.DataType.VARNUMERIC|  
|AdoEnums.DataType.VARWCHAR|  
|AdoEnums.DataType.WCHAR|  
  
## <a name="applies-to"></a>Объект применения  
  
|||  
|-|-|  
|[Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|  
|[Метод CreateRecordset (служба удаленных рабочих столов)](../../../ado/reference/rds-api/createrecordset-method-rds.md)|[Свойство Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)|

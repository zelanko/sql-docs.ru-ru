---
title: DataTypeEnum | Документы Microsoft
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- DataTypeEnum
helpviewer_keywords:
- DataTypeEnum enumeration [ADO]
ms.assetid: 2c57eca6-9336-4b06-ba10-9fef5926b1d0
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5ca60e4fda2319b9b63d7c0b7c0162cfd8027063
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datatypeenum"></a>DataTypeEnum
Указывает тип данных [поле](../../../ado/reference/ado-api/field-object.md), [параметр](../../../ado/reference/ado-api/parameter-object.md), или [свойства](../../../ado/reference/ado-api/property-object-ado.md). В круглых скобках в столбце "Описание" в следующей таблице показан соответствующий индикатор типа OLE DB.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**AdArray**|0x2000|Значение флага всегда в сочетании с другой константой данных типа, указывающее массив другого типа данных. Не применяется к ADOX.|  
|**adBigInt**|20|Показывает, 8 байтовое целое число со знаком (DBTYPE_I8).|  
|**adBinary**|128|Указывает двоичное значение (DBTYPE_BYTES).|  
|**adBoolean**|11|Указывает **логическое** значение (DBTYPE_BOOL).|  
|**adBSTR**|8|Показывает строку, завершающуюся значением null (Юникод) (DBTYPE_BSTR).|  
|**adChapter**|136|Указывает значение Глава 4 байта, определяет строки в набор дочерних строк (DBTYPE_HCHAPTER).|  
|**adChar**|129|Указывает строковое значение (DBTYPE_STR).|  
|**adCurrency**|6|Указывает значение валюты (DBTYPE_CY). Валюта представляет число с фиксированной запятой с четырьмя цифрами справа от десятичной запятой. Он хранится в 8 байтовое целое число со знаком, умноженное на 10 000.|  
|**adDate**|7|Указывает значение даты (DBTYPE_DATE). Дата сохраняется как тип double, целая часть из которых — количество дней, прошедших с 30 декабря 1899 г., а дробная часть которого равна части дня.|  
|**adDBDate**|133|Указывает значение даты (ГГГГММДД) (DBTYPE_DBDATE).|  
|**adDBTime**|134|Указывает значение времени (ЧЧММСС) (DBTYPE_DBTIME).|  
|**adDBTimeStamp**|135|Указывает метку даты и времени (ггггммддччммсс плюс дробного в миллиардных) (DBTYPE_DBTIMESTAMP).|  
|**adDecimal**|14|Указывает точное числовое значение с фиксированной точностью и масштабом (DBTYPE_DECIMAL).|  
|**adDouble**|5|Указывает значение с плавающей запятой двойной точности (DBTYPE_R8).|  
|**adEmpty**|0|Не заданы значения (DBTYPE_EMPTY).|  
|**adError**|10|Указывает 32-битный код ошибки (DBTYPE_ERROR).|  
|**adFileTime**|64|Указывает, 64-разрядное значение, представляющее количество 100-наносекундных интервалов с 1 января 1601 г. (DBTYPE_FILETIME).|  
|**adGUID**|72|Глобально уникальный идентификатор (GUID) (DBTYPE_GUID).|  
|**adIDispatch**|9|Указывает указатель **IDispatch** интерфейс COM-объекта (DBTYPE_IDISPATCH).<br /><br /> **Примечание** этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adInteger**|3|Указывает четырехбайтовое целое число со знаком (DBTYPE_I4).|  
|**adIUnknown**|13|Указывает указатель **IUnknown** интерфейс COM-объекта (DBTYPE_IUNKNOWN).<br /><br /> **Примечание** этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adLongVarBinary**|205|Указывает длинным двоичным значением.|  
|**adLongVarChar**|201|Указывает длинное строковое значение.|  
|**adLongVarWChar**|203|Указывает значение долго символом null строку Юникода.|  
|**adNumeric**|131|Указывает на точное числовое значение с фиксированной точностью и масштабом (DBTYPE_NUMERIC).|  
|**adPropVariant**|138|Указывает автоматизации PROPVARIANT (DBTYPE_PROP_VARIANT).|  
|**adSingle**|4|Указывает значение с плавающей запятой одинарной точности (DBTYPE_R4).|  
|**adSmallInt**|2|Указывает двухбайтное целое число со знаком (DBTYPE_I2).|  
|**adTinyInt**|16|Указывает однобайтовое целое число со знаком (DBTYPE_I1).|  
|**adUnsignedBigInt**|21|Показывает, 8 байтовое целое число (DBTYPE_UI8).|  
|**adUnsignedInt**|19|Указывает четырехбайтовое целое число без знака (DBTYPE_UI4).|  
|**adUnsignedSmallInt**|18|Указывает двухбайтное целое число без знака (DBTYPE_UI2).|  
|**adUnsignedTinyInt**|17|Указывает однобайтовое целое число без знака (DBTYPE_UI1).|  
|**adUserDefined**|132|Указывает пользовательскую переменную (DBTYPE_UDT).|  
|**adVarBinary**|204|Указывает двоичное значение.|  
|**adVarChar**|200|Указывает строковое значение.|  
|**adVariant**|12|Указывает автоматизации **Variant** (DBTYPE_VARIANT).<br /><br /> **Примечание** этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adVarNumeric**|139|Указывает числовое значение.|  
|**AdVarWChar**|202|Указывает строку символов Юникода символом null.|  
|**adWChar**|130|Указывает строку символов Юникода (DBTYPE_WSTR) символом null.|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
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

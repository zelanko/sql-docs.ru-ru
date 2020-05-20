---
title: Дататипинум | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 5d22757951cad59c10bc1d7eea85ea8ee11ed0ad
ms.sourcegitcommit: 6037fb1f1a5ddd933017029eda5f5c281939100c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2020
ms.locfileid: "82757630"
---
# <a name="datatypeenum"></a>DataTypeEnum
Указывает тип данных [поля](../../../ado/reference/ado-api/field-object.md), [параметра](../../../ado/reference/ado-api/parameter-object.md)или [Свойства](../../../ado/reference/ado-api/property-object-ado.md). Соответствующий индикатор типа OLE DB отображается в круглых скобках в столбце Описание следующей таблицы.  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|**адаррай**|0x2000|Значение флага, которое всегда объединяется с другой константой типа данных, которая указывает на массив другого типа данных. Не применяется к ADOX.|  
|**adBigInt**|20|Указывает 8-байтовое целое число со знаком (DBTYPE_I8).|  
|**adBinary**|128|Указывает двоичное значение (DBTYPE_BYTES).|  
|**adBoolean**|11|Указывает **логическое** значение (DBTYPE_BOOL).|  
|**adBSTR**|8|Указывает строку символов (Юникод), завершающуюся нулем (DBTYPE_BSTR).|  
|**adChapter**|136|Указывает 4-байтовое значение главы, определяющее строки в дочернем наборе строк (DBTYPE_HCHAPTER).|  
|**adChar**|129|Указывает строковое значение (DBTYPE_STR).|  
|**adCurrency**|6|Указывает значение валюты (DBTYPE_CY). Currency — это число с фиксированной запятой с четырьмя цифрами справа от десятичной запятой. Он хранится в 8-байтном целом число со знаком, масштабированном на 10 000.|  
|**adDate**|7|Указывает значение даты (DBTYPE_DATE). Дата хранится в виде Double, целой части, равной количеству дней с 30 декабря 1899, и дробной части, которая является долей дня.|  
|**adDBDate**|133|Указывает значение даты (ГГГГММДД) (DBTYPE_DBDATE).|  
|**adDBTime**|134|Указывает значение времени (ЧЧММСС) (DBTYPE_DBTIME).|  
|**adDBTimeStamp**|135|Указывает отметку даты и времени (YYYYMMDDHHMMSS плюс часть в биллионсс) (DBTYPE_DBTIMESTAMP).|  
|**adDecimal**|14|Указывает точное числовое значение с фиксированной точностью и масштабом (DBTYPE_DECIMAL).|  
|**adDouble**|5|Указывает значение с плавающей точкой двойной точности (DBTYPE_R8).|  
|**адемпти**|0|Не указывает значение (DBTYPE_EMPTY).|  
|**adError**|10|Указывает 32-разрядный код ошибки (DBTYPE_ERROR).|  
|**adFileTime**|64|Указывает 64-разрядное значение, представляющее число 100-наносекундных интервалов с 1 января 1601 (DBTYPE_FILETIME).|  
|**adGUID**|72|Указывает глобальный уникальный идентификатор (GUID) (DBTYPE_GUID).|  
|**adIDispatch**|9|Указывает указатель на интерфейс **IDispatch** для COM-объекта (DBTYPE_IDISPATCH).<br /><br /> **Примечание** . Этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adInteger**|3|Указывает 4-байтовое целое число со знаком (DBTYPE_I4).|  
|**adIUnknown**|13|Указывает указатель на интерфейс **IUnknown** для COM-объекта (DBTYPE_IUNKNOWN).<br /><br /> **Примечание** . Этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**адлонгварбинари**|205|Указывает на Длинное двоичное значение.|  
|**adLongVarChar**|201|Указывает длинное строковое значение.|  
|**adLongVarWChar**|203|Указывает длинное строковое значение Юникода, завершающееся нулем.|  
|**adNumeric**|131|Указывает точное числовое значение с фиксированной точностью и масштабом (DBTYPE_NUMERIC).|  
|**adPropVariant**|138|Указывает ПРОПВАРИАНТ автоматизации (DBTYPE_PROP_VARIANT).|  
|**adSingle**|4|Указывает значение с плавающей точкой одиночной точности (DBTYPE_R4).|  
|**adSmallInt**|2|Указывает двухбайтовое целое число со знаком (DBTYPE_I2).|  
|**adTinyInt**|16|Указывает Однобайтовое целое число со знаком (DBTYPE_I1).|  
|**adUnsignedBigInt**|21|Указывает целое число без знака размером 8 байт (DBTYPE_UI8).|  
|**adUnsignedInt**|19|Указывает целое число без знака длиной 4 байта (DBTYPE_UI4).|  
|**adUnsignedSmallInt**|18|Указывает двухбайтовое целое число без знака (DBTYPE_UI2).|  
|**adUnsignedTinyInt**|17|Указывает Однобайтовое целое число без знака (DBTYPE_UI1).|  
|**adUserDefined**|132|Указывает определяемую пользователем переменную (DBTYPE_UDT).|  
|**адварбинари**|204|Указывает двоичное значение.|  
|**адварчар**|200|Указывает строковое значение.|  
|**adVariant**|12|Указывает **вариант** автоматизации (DBTYPE_VARIANT).<br /><br /> **Примечание** . Этот тип данных в настоящее время не поддерживается ADO. Использование может привести к непредсказуемым результатам.|  
|**adVarNumeric**|139|Указывает числовое значение.|  
|**адварвчар**|202|Указывает строку символов в Юникоде, завершающуюся нулем.|  
|**adWChar**|130|Указывает строку символов в Юникоде, завершающуюся нулем (DBTYPE_WSTR).|  
  
## <a name="adowfc-equivalent"></a>Эквивалент ADO/WFC  
 Пакет: **com. MS. WFC. Data**  
  
|Константа|  
|--------------|  
|Адоенумс. DataType. ARRAY|  
|Адоенумс. DataType. BIGINT|  
|Адоенумс. Тип_данных. BINARY|  
|Адоенумс. DataType. BOOLEAN|  
|Адоенумс. DataType. BSTR|  
|Адоенумс. Тип_данных. CHAPTER|  
|Адоенумс. DataType. CHAR|  
|Адоенумс. Тип_данных. CURRENCY|  
|Адоенумс. Тип_данных. DATE|  
|Адоенумс. DataType. ДБДАТЕ|  
|Адоенумс. DataType. ДБТИМЕ|  
|Адоенумс. DataType. DBTIMESTAMP|  
|Адоенумс. Тип_данных. DECIMAL|  
|Адоенумс. DataType. DOUBLE|  
|Адоенумс. Тип_данных. EMPTY|  
|Адоенумс. DataType. ERROR|  
|Адоенумс. DataType. FILETIME|  
|Адоенумс. DataType. GUID|  
|Адоенумс. DataType. IDISPATCH|  
|Адоенумс. DataType. ЦЕЛОе число|  
|Адоенумс. DataType. IUNKNOWN|  
|Адоенумс. DataType. LONGVARBINARY|  
|Адоенумс. DataType. LONGVARCHAR|  
|Адоенумс. DataType. ЛОНГВАРВЧАР|  
|Адоенумс. DataType. NUMERIC|  
|Адоенумс. DataType. ПРОПВАРИАНТ|  
|Адоенумс. Тип_данных. SINGLE|  
|Адоенумс. DataType. SMALLINT|  
|Адоенумс. DataType. TINYINT|  
|Адоенумс. DataType. UNSIGNEDBIGINT|  
|Адоенумс. DataType. UNSIGNEDINT|  
|Адоенумс. DataType. UNSIGNEDSMALLINT|  
|Адоенумс. DataType. UNSIGNEDTINYINT|  
|Адоенумс. DataType. ПОЛЬЗОВАТЕЛЯОПРЕДЕЛЕННЫЕ|  
|Адоенумс. DataType. VARBINARY|  
|Адоенумс. DataType. VARCHAR|  
|Адоенумс. DataType. VARIANT|  
|Адоенумс. DataType. типа VARNUMERIC|  
|Адоенумс. DataType. ВАРВЧАР|  
|Адоенумс. DataType. WCHAR|  
  
## <a name="applies-to"></a>Применяется к  
  
|||  
|-|-|  
|[Метод Append (ADO)](../../../ado/reference/ado-api/append-method-ado.md)|[Метод CreateParameter (ADO)](../../../ado/reference/ado-api/createparameter-method-ado.md)|  
|[Метод CreateRecordset (служба удаленных рабочих столов)](../../../ado/reference/rds-api/createrecordset-method-rds.md)|[Свойство Type (ADO)](../../../ado/reference/ado-api/type-property-ado.md)|

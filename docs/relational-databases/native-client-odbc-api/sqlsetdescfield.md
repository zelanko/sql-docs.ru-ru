---
title: СЗЛСетДескФилд Документы Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f699610ce3aac1443439aa5d293e92104f3033d5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292146"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Для установки полей дескриптора для параметров, ценных на стол, и столовых столбцов, можно использовать полей дескриптора. Для получения информации о доступных полях [см.](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) [Descriptor Fields for Table-Valued Parameter Constituent Columns](../../relational-databases/native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)  
  
## <a name="remarks"></a>Remarks  
 Столбцы возвращающих табличное значение параметров доступны только в том случае, когда в поле заголовка дескриптора SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер записи, имеющей тип SQL_DESC_TYPE со значением SQL_SS_TABLE. Дополнительные сведения об атрибуте SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 При попытке установить SQL_SOPT_SS_PARAM_FOCUS к облачному параметру, который не является параметром, ценным на стол, s'LSetStmtAttr возвращается SQL_ERROR, и создается диагностическая запись с помощью S'LSTATE S HY024 и сообщения "Недействительное значение атрибута". Если возвращается значение SQL_ERROR, то атрибут SQL_SOPT_SS_PARAM_FOCUS не меняется.  
  
 Установка атрибута SQL_SOPT_SS_PARAM_FOCUS в значение 0 восстанавливает доступ к записям дескриптора для параметров.  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLSetDescField улучшенных функций работы с данными в формате даты-времени  
 Функции работы с данными в формате даты-времени были расширены в ODBC. Для получения информации о поле дескриптора, предусмотренном для новых типов дат/времени, [см.](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md)  
  
 Для получения дополнительной информации см [&#41;&#40;. ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>Поддержка функцией SQLSetDescField определяемых пользователем типов больших данных CLR  
 S'LSetDescfield поддерживает большие типы, определяемые пользователями CLR (UDT). Для получения дополнительной информации смотрите [большие типы, определяемые пользователями CLR, &#40;&#41;ODBC. ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>Поддержка функцией SQLSetDescField разреженных столбцов  
 Для установки SQL_SOPT_SS_NAME_SCOPE в дескрипторе параметра приложения (APD) можно использовать SQL_SOPT_SS_NAME_SCOPE значений, SQL_SS_NAME_SCOPE_EXTENDED и SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.  
  
 Для получения дополнительной информации см. [Sparse колонки поддержка &#40;ODBC&#41;](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [СЗЛСетДескФилд](https://go.microsoft.com/fwlink/?LinkId=80705)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

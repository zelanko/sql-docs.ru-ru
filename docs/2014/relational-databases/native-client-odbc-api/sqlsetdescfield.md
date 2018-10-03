---
title: SQLSetDescField | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 64eb7b3dc6f058d5f061f4c015105ba4fc44f183
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48206764"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
  SQLSetDescField позволяют задать поля дескриптора для возвращающих табличные значения параметров и столбцов возвращающих табличные значения. Сведения о доступных полях см. в разделе [поля дескрипторов возвращающего табличное значение параметра](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) и [поля дескриптора для столбцов составные возвращающего табличное значение параметра](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).  
  
## <a name="remarks"></a>Примечания  
 Столбцы возвращающих табличное значение параметров доступны только в том случае, когда в поле заголовка дескриптора SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер записи, имеющей тип SQL_DESC_TYPE со значением SQL_SS_TABLE. Дополнительные сведения об атрибуте SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Если попытки для присвоения параметру SQL_SOPT_SS_PARAM_FOCUS порядковый номер параметра, который не является параметром с табличным, SQLSetStmtAttr возвращает значение SQL_ERROR и создается диагностическая запись создается с кодом SQLSTATE = HY024 и сообщением «недопустимое значение атрибута». Если возвращается значение SQL_ERROR, то атрибут SQL_SOPT_SS_PARAM_FOCUS не меняется.  
  
 Установка атрибута SQL_SOPT_SS_PARAM_FOCUS в значение 0 восстанавливает доступ к записям дескриптора для параметров.  
  
 Дополнительные сведения о возвращающих табличные значения параметров, см. в разделе [возвращающего табличное значение параметров &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLSetDescField улучшенных функций работы с данными в формате даты-времени  
 Функции работы с данными в формате даты-времени были расширены в ODBC. Сведения о поле дескриптора, предоставленного для типов новые даты и времени, см. в разделе [метаданные параметров и результатов](../native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Дополнительные сведения см. в разделе [время улучшения функций даты и &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>Поддержка функцией SQLSetDescField определяемых пользователем типов больших данных CLR  
 SQLSetDescField поддерживает большие определяемые пользователем типы CLR (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>Поддержка функцией SQLSetDescField разреженных столбцов  
 SQLSetDecField можно использовать для задания атрибута SQL_SOPT_SS_NAME_SCOPE в дескрипторе параметра приложения (APD) для значений SQL_SS_NAME_SCOPE_EXTENDED и SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.  
  
 Дополнительные сведения см. в разделе [Поддержка разреженных столбцов &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLSetDescField](http://go.microsoft.com/fwlink/?LinkId=80705)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  

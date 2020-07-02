---
title: SQLSetDescField | Документация Майкрософт
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
ms.openlocfilehash: a2c32ec320a94dad7740bfd32d30057941ee8b71
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85751860"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asdw-pdw.md)]

  SQLSetDescField можно использовать для задания полей дескриптора для возвращающих табличное значение параметров и столбцов возвращающих табличное значение параметров. Сведения о доступных полях см. в разделе [поля дескриптора возвращающего](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) табличное значение параметра и [поля дескриптора для составных столбцов возвращающего](../../relational-databases/native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)табличное значение параметра.  
  
## <a name="remarks"></a>Примечания  
 Столбцы возвращающих табличное значение параметров доступны только в том случае, когда в поле заголовка дескриптора SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер записи, имеющей тип SQL_DESC_TYPE со значением SQL_SS_TABLE. Дополнительные сведения об атрибуте SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Если предпринимается попытка задать SQL_SOPT_SS_PARAM_FOCUS порядковому номеру параметра, который не является возвращающим табличное значение параметром, SQLSetStmtAttr возвращает SQL_ERROR, а запись диагностики создается с параметром SQLSTATE = HY024 и сообщением "Недопустимый атрибут value". Если возвращается значение SQL_ERROR, то атрибут SQL_SOPT_SS_PARAM_FOCUS не меняется.  
  
 Установка атрибута SQL_SOPT_SS_PARAM_FOCUS в значение 0 восстанавливает доступ к записям дескриптора для параметров.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLSetDescField улучшенных функций работы с данными в формате даты-времени  
 Функции работы с данными в формате даты-времени были расширены в ODBC. Сведения о поле дескриптора, предоставленном для новых типов даты и времени, см. в разделе [метаданные параметров и результатов](../../relational-databases/native-client-odbc-date-time/metadata-parameter-and-result.md).  
  
 Дополнительные сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>Поддержка функцией SQLSetDescField определяемых пользователем типов больших данных CLR  
 SQLSetDescField поддерживает большие определяемые пользователем типы данных CLR (UDT). Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>Поддержка функцией SQLSetDescField разреженных столбцов  
 Склсетдекфиелд можно использовать для установки SQL_SOPT_SS_NAME_SCOPE в дескрипторе параметра приложения (APD) на значения SQL_SS_NAME_SCOPE_EXTENDED и SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.  
  
 Дополнительные сведения см. в разделе [Поддержка разреженных столбцов &#40;&#41;ODBC ](../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

---
title: SQLGetStmtAttr | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 198c3c8e5752aebc58726b2e7478632adf2c1bd0
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73786283"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] расширяет SQLGetStmtAttr для предоставления атрибутов инструкций, относящихся к драйверу.  
  
 Функция[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) перечисляет атрибуты инструкции, которые можно как считывать, так и изменять. В данном разделе приводятся атрибуты инструкции только для чтения.  
  
## <a name="sql_sopt_ss_current_command"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 Атрибут SQL_SOPT_SS_CURRENT_COMMAND предоставляет текущую команду пакета команд. Возвращение является целым числом, указывающим расположение команды в пакете. Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
## <a name="sql_sopt_ss_nocount_status"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 Атрибут SQL_SOPT_SS_NOCOUNT_STATUS указывает текущее значение параметра NOCOUNT, управляющего формированием отчета [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] о числе строк, затронутых инструкцией при вызове метода [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) . Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|Значение|Описание|  
|-----------|-----------------|  
|SQL_NC_OFF|Значение NOCOUNT — OFF. SQLRowCount возвращает число затронутых строк.|  
|SQL_NC_ON|Значение NOCOUNT — ON. Число затронутых строк не возвращается функцией SQLRowCount, а возвращаемое значение равно 0.|  
  
 Если SQLRowCount возвращает 0, приложение должно протестировать SQL_SOPT_SS_NOCOUNT_STATUS. Если возвращается SQL_NC_ON, значение 0 из SQLRowCount указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не вернул число строк. Если возвращается SQL_NC_OFF, это означает, что параметр NOCOUNT отключен и значение 0 из SQLRowCount указывает на то, что инструкция не повлияла ни на какие строки.  
  
 Приложения не должны отображать значение SQLRowCount, если SQL_SOPT_SS_NOCOUNT_STATUS SQL_NC_OFF. Большие пакеты или хранимые процедуры могут содержать несколько инструкций SET NOCOUNT, следовательно, нельзя предположить, что SQL_SOPT_SS_NOCOUNT_STATUS остается неизменным. Этот параметр следует проверять каждый раз, когда SQLRowCount возвращает 0.  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a>Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT возвращает текст сообщения в ответ на запрошенное уведомление о запросе.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr и возвращающие табличное значение параметры  
 SQLGetStmtAttr можно вызвать, чтобы получить значение SQL_SOPT_SS_PARAM_FOCUS в дескрипторе параметра приложения (APD) при работе с возвращающими табличные значения параметрами. Дополнительные сведения о SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также раздел  
   [функции SQLSetStmtAttr](https://go.microsoft.com/fwlink/?LinkId=59370)  
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

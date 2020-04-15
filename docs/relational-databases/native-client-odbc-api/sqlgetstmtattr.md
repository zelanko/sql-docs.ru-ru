---
title: СЗЛГетстмттр Документы Майкрософт
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
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f59b7f006387beea3d213b7f120e567487232e69
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282102"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC расширяет возможность предоставления атрибутов оператора для конкретных драйверов.  
  
 Функция[SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) перечисляет атрибуты инструкции, которые можно как считывать, так и изменять. В данном разделе приводятся атрибуты инструкции только для чтения.  
  
## <a name="sql_sopt_ss_current_command"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 Атрибут SQL_SOPT_SS_CURRENT_COMMAND предоставляет текущую команду пакета команд. Возвращение является целым числом, указывающим расположение команды в пакете. Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
## <a name="sql_sopt_ss_nocount_status"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 Атрибут SQL_SOPT_SS_NOCOUNT_STATUS указывает текущее значение параметра NOCOUNT, управляющего формированием отчета [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] о числе строк, затронутых инструкцией при вызове метода [SQLRowCount](../../relational-databases/native-client-odbc-api/sqlrowcount.md) . Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|Значение|Описание|  
|-----------|-----------------|  
|SQL_NC_OFF|Значение NOCOUNT — OFF. S'LRowCount возвращает количество затронутых строк.|  
|SQL_NC_ON|Значение NOCOUNT — ON. Количество затронутых строк не возвращается S'LRowCount, а возвращенное значение составляет 0.|  
  
 Если S'LRowCount возвращает 0, приложение должно проверить SQL_SOPT_SS_NOCOUNT_STATUS. При возврате SQL_NC_ON значение 0 от S'LRowCount указывает только на то, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не вернулось количество строк. Если возвращается SQL_NC_OFF, значит параметр NOCOUNT отключен и значение 0, возвращаемое функцией SQLRowCount, указывает, что инструкция не затронула ни одной строки.  
  
 Приложения не должны отображать значение, возвращаемое функцией SQLRowCount, если параметр SQL_SOPT_SS_NOCOUNT_STATUS установлен в значение SQL_NC_OFF. Большие пакеты или хранимые процедуры могут содержать несколько инструкций SET NOCOUNT, следовательно, нельзя предположить, что SQL_SOPT_SS_NOCOUNT_STATUS остается неизменным. Эта опция должна быть проверена каждый раз, когда S'LRowCount возвращает 0.  
  
## <a name="sql_sopt_ss_querynotification_msgtext"></a>Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT возвращает текст сообщения в ответ на запрошенное уведомление о запросе.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr и возвращающие табличное значение параметры  
 Можно вызвать значение SQL_SOPT_SS_PARAM_FOCUS в дескрипторе параметра приложения (APD) при работе с параметрами, оцениваемыми таблицей. Дополнительные сведения о SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md).  
  
 Для получения дополнительной информации о параметрах, ценных на стол, с [&#41;&#40;м. ](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
## <a name="see-also"></a>См. также:  
 [Функция СЗЛСетСтматтатр](https://go.microsoft.com/fwlink/?LinkId=59370)   
 [ODBC API Implementation Details](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

---
title: SQLGetStmtAttr | Документы Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetStmtAttr function
ms.assetid: e64f4f94-eb73-4477-9745-080b6cbdc751
caps.latest.revision: 43
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 5c6f1220685b2e9f72df52ddea9c1f676453b856
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192448"
---
# <a name="sqlgetstmtattr"></a>SQLGetStmtAttr
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Драйвер ODBC собственного клиента расширяет SQLGetStmtAttr для предоставления атрибутов инструкции, относящиеся к драйверу.  
  
 [SQLSetStmtAttr](sqlsetstmtattr.md) Перечисляет атрибуты инструкции, которые также присутствуют чтения и записи. В данном разделе приводятся атрибуты инструкции только для чтения.  
  
## <a name="sqlsoptsscurrentcommand"></a>SQL_SOPT_SS_CURRENT_COMMAND  
 Атрибут SQL_SOPT_SS_CURRENT_COMMAND предоставляет текущую команду пакета команд. Возвращение является целым числом, указывающим расположение команды в пакете. Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
## <a name="sqlsoptssnocountstatus"></a>SQL_SOPT_SS_NOCOUNT_STATUS  
 Атрибут SQL_SOPT_SS_NOCOUNT_STATUS указывает текущее значение параметра NOCOUNT параметра, управляющим ли [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] сообщает количество строк, затронутых инструкцией при [SQLRowCount](sqlrowcount.md) вызывается. Значение аргумента *ValuePtr* имеет тип SQLLEN.  
  
|Значение|Описание|  
|-----------|-----------------|  
|SQL_NC_OFF|Значение NOCOUNT — OFF. SQLRowCount возвращает число затронутых строк.|  
|SQL_NC_ON|Значение NOCOUNT — ON. Число обработанных строк не возвращается, то эта функция, и возвращаемое значение равно 0.|  
  
 Если SQLRowCount возвращает 0, приложение должно проверить SQL_SOPT_SS_NOCOUNT_STATUS. Если возвращается sql_nc_on, значение 0 от SQLRowCount только указывает, что [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не вернул количество строк. Если возвращается sql_nc_off, это означает, что NOCOUNT отключен и значение 0 от SQLRowCount указывает, что инструкция не обработала все строки.  
  
 Приложения не должны отображать значение SQLRowCount, когда sql_sopt_ss_nocount_status установлен в значение SQL_NC_OFF. Большие пакеты или хранимые процедуры могут содержать несколько инструкций SET NOCOUNT, следовательно, нельзя предположить, что SQL_SOPT_SS_NOCOUNT_STATUS остается неизменным. Этот параметр необходимо проверять каждый раз, то эта функция возвращает 0.  
  
## <a name="sqlsoptssquerynotificationmsgtext"></a>Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT  
 Атрибут SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT возвращает текст сообщения в ответ на запрошенное уведомление о запросе.  
  
## <a name="sqlgetstmtattr-and-table-valued-parameters"></a>SQLGetStmtAttr и возвращающие табличное значение параметры  
 SQLGetStmtAttr может вызываться для получения значения SQL_SOPT_SS_PARAM_FOCUS в дескрипторе параметра приложения (APD) при работе с табличное значение параметров. Дополнительные сведения о SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [Функция SQLSetStmtAttr](http://go.microsoft.com/fwlink/?LinkId=59370)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
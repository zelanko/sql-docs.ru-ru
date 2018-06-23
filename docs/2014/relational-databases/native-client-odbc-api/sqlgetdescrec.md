---
title: SQLGetDescRec | Документы Microsoft
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
helpviewer_keywords:
- SQLGetDescRec function
ms.assetid: f3389ff2-f3be-4035-9fb5-c9ebc2f15025
caps.latest.revision: 18
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 201e30880c289636ac550559b0678a4e94427253
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36109716"
---
# <a name="sqlgetdescrec"></a>SQLGetDescRec
  В этом разделе обсуждаются SQLGetDescRec функциональные возможности, относящиеся к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="sqlgetdescrec-and-table-valued-parameters"></a>Функция SQLGetDescRec и возвращающие табличные значения параметры  
 SQLGetDescRec можно использовать для получения значений атрибутов возвращающих табличные значения параметров и столбцов возвращающих табличные значения параметров. *RecNumber* соответствующий параметр SQLGetDescRec *ParameterNumber* функции SQLBindParameter.  
  
 Столбцы возвращающих табличное значение параметров доступны только в том случае, когда в поле заголовка дескриптора SQL_SOPT_SS_PARAM_FOCUS задан порядковый номер записи, имеющей тип SQL_DESC_TYPE со значением SQL_SS_TABLE. Дополнительные сведения о столбце SQL_SOPT_SS_PARAM_FOCUS см. в разделе [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 SQLGetDescRec возвращает следующие данные:  
  
|Параметр|Возвращающий табличное значение параметр|Столбцы возвращающих табличные значения параметров и других параметров|  
|---------------|-----------------------------|----------------------------------------------------------|  
|*Название*|Имя параметра для вызова хранимой процедуры; в противном случае строка длины 0.|Имя столбца возвращающих табличные значения параметров.|  
|*TypePtr*|SQL_DESC_TYPE. Для возвращающих табличные значения параметров — SQL_SS_TABLE.|SQL_DESC_TYPE|  
|*SubTypePtr*|Не определено.|SQL_DESC_DATETIME_INTERVAL_CODE (для записей типа SQL_DATETIME или SQL_INTERVAL).|  
|*LengthPtr*|0|SQL_DESC_OCTET_LENGTH|  
|*PrecisionPtr*|0|SQL_DESC_PRECISION|  
|*ScalePtr*|0|SQL_DESC_SCALE|  
|*NullablePtr*|1|SQL_DESC_NULLABLE|  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLGetDescRec улучшенных функций даты и времени  
 Для типов даты-времени возвращаются следующие значения.  
  
||*TypePtr*|*SubTypePtr*|*LengthPtr*|*PrecisionPtr*|*ScalePtr*|  
|-|---------------|------------------|-----------------|--------------------|----------------|  
|DATETIME|SQL_DATETIME|SQL_CODE_TIMESTAMP|4|3|3|  
|smalldatetime|SQL_DATETIME|SQL_CODE_TIMESTAMP|8|0|0|  
|Дата|SQL_DATETIME|SQL_CODE_DATE|6|0|0|  
|time|SQL_SS_TIME2|0|10|0..7|0..7|  
|datetime2|SQL_DATETIME|SQL_CODE_TIMESTAMP|16|0..7|0..7|  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET|0|20|0..7|0..7|  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgetdescrec-support-for-large-clr-udts"></a>Поддержка функцией SQLGetDescRec больших определяемых пользователем типов (UDT) среды CLR  
 Функция `SQLGetDescRec` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLGetDescRec](http://go.microsoft.com/fwlink/?LinkId=80707)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
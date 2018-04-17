---
title: SQLPutData | Документы Microsoft
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: native-client-odbc-api
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apitype: DLLExport
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
caps.latest.revision: 49
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 8d9dffe53e18bf63951f6204435bd684844adc61
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sqlputdata"></a>SQLPutData
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Применяются следующие ограничения при использовании SQLPutData для отправки более 65 535 байт данных (для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] версии 4.21a) или 400 КБ данных (SQL Server версии 6.0 и более поздние версии) для SQL_LONGVARCHAR (**текст**), SQL_WLONGVARCHAR (**ntext**) или SQL_LONGVARBINARY (**изображения**) столбца:  
  
-   Указанный параметр может иметь *insert_value* в инструкции INSERT.  
  
-   Указанный параметр может иметь *выражение* в предложении SET инструкции UPDATE.  
  
 Отмена последовательности вызовов SQLPutData, которые предоставляют данные в блоки на сервер под управлением [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] вызывает частичное обновление значений в столбце при использовании версии 6.5 или более ранней версии. **Текст**, **ntext**, или **изображения** имеет значение столбца, который был указан при вызове SQLCancel на промежуточное значение заполнителя.  
  
> [!NOTE]  
>  Драйвер ODBC собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживает соединение с версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 и более ранней.  
  
## <a name="diagnostics"></a>Диагностика  
 Имеется один [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] конкретных SQLSTATE собственного клиента для SQLPutData:  
  
|SQLSTATE|Ошибка|Описание|  
|--------------|-----------|-----------------|  
|22026|Строковые данные, несовпадение длины|Если длина данных в байтах для отправляемых была указана приложением, например, с SQL_LEN_DATA_AT_EXEC (*n*) где *n* больше 0, общее число байтов, передаваемых приложением через SQLPutData должно соответствовать указанной длине.|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a>Функция SQLPutData и параметры, возвращающие табличные значения  
 SQLPutData используется приложением при использовании переменной привязки строки с табличное значение параметров. *StrLen_Or_Ind* параметр указывает, что она готова для сбора данных для следующей строки или строк данных возвращающих табличные значения параметров драйвера или что больше нет строк доступны:  
  
-   Значение, большее 0, указывает на доступность следующего набора значений строки.  
  
-   Значение 0 указывает, что строк для отправки больше нет.  
  
-   Значение меньше 0 является ошибочным и приводит к внесению в журнал диагностической записи со значением SQLState, равным HY090, и сообщением «Недопустимая длина строки или буфера».  
  
 *DataPtr* параметр учитывается, но должно быть присвоено значение отличное от NULL. Дополнительные сведения см в подразделе о привязка строк возвращающего табличное значение Параметра переменной в [привязки и Data Transfer of Table-Valued параметры и значения столбцов](../../relational-databases/native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).  
  
 Если *StrLen_Or_Ind* имеет значение, отличное от SQL_DEFAULT_PARAM, или число между 0 и SQL_PARAMSET_SIZE (то есть *ColumnSize* функции SQLBindParameter), является ошибкой. В результате этой ошибки функция SQLPutData возвращает SQL_ERROR: SQLSTATE = HY090, «Недопустимая длина строки или буфера».  
  
 Дополнительные сведения о возвращающих табличные значения параметров см. в разделе [табличное значение параметры & #40; ODBC & #41;](../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a>Поддержка функции SQLPutData для улучшенных функций даты-времени  
 Значения параметров типов даты времени преобразуются, как описано в [преобразования из C в SQL](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования & #40; ODBC & #41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a>Поддержка функции SQLPutData для больших определяемых пользователем типов данных CLR  
 **SQLPutData** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы & #40; ODBC & #41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLPutData, функция](http://go.microsoft.com/fwlink/?LinkId=59365)   
 [Сведения о реализации API-интерфейса ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

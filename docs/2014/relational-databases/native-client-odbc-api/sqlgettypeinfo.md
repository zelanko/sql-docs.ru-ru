---
title: SQLGetTypeInfo | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: rothja
ms.author: jroth
ms.openlocfilehash: f995e3c288435ed55d2f1496894f73409496c06d
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022033"
---
# <a name="sqlgettypeinfo"></a>SQLGetTypeInfo
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Драйвер ODBC для собственного клиента сообщает дополнительный столбец USERTYPE в результирующем наборе `SQLGetTypeInfo` . USERTYPE возвращает определение типа данных DB-Library. Этот столбец полезен разработчикам, которые переносят существующие приложения DB-Library в ODBC.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] рассматривает идентификатор как атрибут, а в ODBC он считается типом данных. Чтобы устранить это несоответствие, `SQLGetTypeInfo` возвращает типы данных: **интидентити**, **смаллинтидентити**, **тининтидентити**, **деЦималидентити**и **нумериЦидентити**. `SQLGetTypeInfo`Столбец результирующего набора AUTO_UNIQUE_VALUE сообщает значение true для этих типов данных.  
  
 Для типа **varchar**, **nvarchar** и **varbinary**драйвер ODBC для собственного клиента по-своемуу [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] отчету 8000, 4000 и 8000 соответственно для COLUMN_SIZE значения, хотя на самом деле он не ограничен. Это делается в целях обратной совместимости.  
  
 Для типа данных **XML** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC для собственного клиента сообщает SQL_SS_LENGTH_UNLIMITED для COLUMN_SIZE, чтобы обозначить неограниченный размер.  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a>SQLGetTypeInfo и параметры, возвращающие табличные значения  
 Тип таблицы для возвращающих табличное значение параметров фактически является мета-типом, т. е. типом, используемым для определения других типов. Поэтому он не должен предоставляться через SQLGetTypeInfo. Для получения метаданных для табличных типов, используемых с возвращающими табличное значение параметрами, приложения должны использовать SQLTables, а не SQLGetTypeInfo.  
  
 Дополнительные сведения о получении метдата для возвращающих табличное значение параметров см. в разделе [атрибуты инструкций, влияющие на возвращающие](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)табличное значение параметры.  
  
 Дополнительные сведения о возвращающих табличное значение параметрах см. в разделе [возвращающие табличное значение параметры &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a>Поддержка SQLGetTypeInfo для улучшенных функций даты-времени  
 Сведения о значениях, возвращаемых для типов даты-времени, см. в разделе [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).  
  
 Дополнительные общие сведения см. в разделе [улучшения даты и времени &#40;&#41;ODBC ](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a>Поддержка SQLGetTypeInfo для больших определяемых пользователем типов данных среды CLR  
 Функция `SQLGetTypeInfo` поддерживает определяемые пользователем типы больших данных CLR. Дополнительные сведения см. в разделе [большие определяемые пользователем типы данных CLR &#40;&#41;ODBC ](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [Функция SQLGetTypeInfo](https://go.microsoft.com/fwlink/?LinkId=59356)   
 [ODBC API Implementation Details](odbc-api-implementation-details.md)  
  
  

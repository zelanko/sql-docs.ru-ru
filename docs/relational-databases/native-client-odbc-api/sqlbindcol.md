---
title: "SQLBindCol | Документы Microsoft"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-api
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
apitype: DLLExport
helpviewer_keywords: SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
caps.latest.revision: "39"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a04abf574a87e25f06ccc26a3e73bdd8cdb2cb98
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="sqlbindcol"></a>SQLBindCol
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Как правило, рассмотрите возможность использования **SQLBindCol** для преобразования данных. Преобразования привязки являются клиентскими процессами, поэтому, например, получение значения с плавающей запятой, связанного с символьным столбцом, вынуждает драйвер выполнить локальное преобразование «плавающая запятая в символ» при выборке строки. Функция [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT может использоваться для размещения затрат преобразования данных на сервере.  
  
 Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может возвращать несколько результирующих наборов для одной инструкции. Каждый результирующий набор должен быть привязан отдельно. Дополнительные сведения о привязке для нескольких результирующих наборов см. в разделе [SQLMoreResults](../../relational-databases/native-client-odbc-api/sqlmoreresults.md).  
  
 Разработчик может привязать столбцы к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-определенные типы данных C помощью *TargetType* значение **SQL_C_BINARY**. Столбцы, привязанные к типам, зависящим от служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не могут быть перенесены. Определенные типы данных ODBC языка C, зависящие от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], совпадают с определениями типов для DB-Library, и разработчики приложений переноса DB-Library могут воспользоваться этой возможностью.  
  
 Отчет об усечении данных является ресурсоемким процессом для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Усечения можно избежать с помощью гарантии того, что все буферы связанных данных достаточно широки для возвращения данных. Для символьных данных ширина должна включать пространство для признака конца строки при использовании поведения драйвера по умолчанию для завершения строки. Например, привязка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** массив результатов пять символов в усечения для каждого значения столбца. Привязка одинакового столбца к массиву из шести символов позволит избежать усечения путем предоставления элемента символа для хранения признака конца NULL. [SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md) можно использовать для эффективного получения длинных символьных и двоичных данных без усечения.  
  
 Для типов данных больших значений, если предоставленный пользователем буфер не является достаточным для хранения всего значения столбца **SQL_SUCCESS_WITH_INFO** возвращается и «строковые данные; усечение справа» предупреждение. **StrLen_or_IndPtr** аргумент будет содержать число символов или байтов, сохраненного в буфере.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLBindCol улучшенных возможностей работы с данными в формате даты-времени  
 Значения результирующих столбцов типов даты времени преобразуются, как описано в [преобразования из SQL в C](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Обратите внимание, что для получения time и datetimeoffset столбцов, как их соответствующие структуры (**SQL_SS_TIME2_STRUCT** и **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType*должен быть указан как **SQL_C_DEFAULT** или **SQL_C_BINARY**.  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Поддержка функцией SQLBindCol определяемых пользователем типов больших данных CLR  
 **SQLBindCol** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40; ODBC &#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также:  
 [SQLBindCol, функция](http://go.microsoft.com/fwlink/?LinkId=59327)   
 [Подробные сведения о реализации API-интерфейсов ODBC](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  

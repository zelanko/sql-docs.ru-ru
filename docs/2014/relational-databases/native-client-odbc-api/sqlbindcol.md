---
title: SQLBindCol | Документы Microsoft
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
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
caps.latest.revision: 39
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2bd30b241f36a8650408fc83142c18558951333b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36194023"
---
# <a name="sqlbindcol"></a>SQLBindCol
  Как правило, рассмотрите возможность использования **SQLBindCol** для преобразования данных. Преобразования привязки являются клиентскими процессами, поэтому, например, получение значения с плавающей запятой, связанного с символьным столбцом, вынуждает драйвер выполнить локальное преобразование «плавающая запятая в символ» при выборке строки. Функция [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT может использоваться для размещения затрат преобразования данных на сервере.  
  
 Экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может возвращать несколько результирующих наборов для одной инструкции. Каждый результирующий набор должен быть привязан отдельно. Дополнительные сведения о привязке для нескольких результирующих наборов см. в разделе [SQLMoreResults](sqlmoreresults.md).  
  
 Разработчик может привязать столбцы к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-определенные типы данных C помощью *TargetType* значение `SQL_C_BINARY`. Столбцы, привязанные к типам, зависящим от служб [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], не могут быть перенесены. Определенные типы данных ODBC языка C, зависящие от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], совпадают с определениями типов для DB-Library, и разработчики приложений переноса DB-Library могут воспользоваться этой возможностью.  
  
 Отчет об усечении данных является ресурсоемким процессом для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] драйвер ODBC собственного клиента. Усечения можно избежать с помощью гарантии того, что все буферы связанных данных достаточно широки для возвращения данных. Для символьных данных ширина должна включать пространство для признака конца строки при использовании поведения драйвера по умолчанию для завершения строки. Например, привязка [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** массив результатов пять символов в усечения для каждого значения столбца. Привязка одинакового столбца к массиву из шести символов позволит избежать усечения путем предоставления элемента символа для хранения признака конца NULL. [SQLGetData](sqlgetdata.md) можно использовать для эффективного получения длинных символьных и двоичных данных без усечения.  
  
 Если предоставленный пользователем буфер не имеет достаточного объема для хранения всего значения столбца, то для типов данных больших значений возвращается `SQL_SUCCESS_WITH_INFO` и выводится предупреждение «строковые данные; усечение справа». Аргумент `StrLen_or_IndPtr` будет содержать число символов или байтов, содержащихся в буфере.  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a>Поддержка функцией SQLBindCol улучшенных возможностей работы с данными в формате даты-времени  
 Значения результирующих столбцов типов даты времени преобразуются, как описано в [преобразования из SQL в C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Обратите внимание, что для получения time и datetimeoffset столбцов, как их соответствующие структуры (`SQL_SS_TIME2_STRUCT` и **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* должен быть указан как `SQL_C_DEFAULT` или `SQL_C_BINARY`.  
  
 Дополнительные сведения см. в разделе [даты и времени усовершенствования &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a>Поддержка функцией SQLBindCol определяемых пользователем типов больших данных CLR  
 **SQLBindCol** поддерживает большие определяемые пользователем типы (UDT). Дополнительные сведения см. в разделе [Large CLR User-Defined типы &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).  
  
## <a name="see-also"></a>См. также  
 [SQLBindCol, функция](http://go.microsoft.com/fwlink/?LinkId=59327)   
 [Подробные сведения о реализации API-интерфейсов ODBC](odbc-api-implementation-details.md)  
  
  
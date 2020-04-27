---
title: Улучшения даты и времени (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d56689bb045a6540bfdfbb9c7147dc34db110bde
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "63207005"
---
# <a name="date-and-time-improvements-odbc"></a>Улучшения функций даты и времени (ODBC)
  В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены новые типы данных даты и времени. В этом разделе описывается, как эти новые типы предоставляются как расширения [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в собственном клиенте. Общие сведения о поддержке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента для новых типов данных даты и времени см. в разделе [улучшения даты и времени](../native-client/features/date-and-time-improvements.md). Пример, демонстрирующий поддержку даты и времени ODBC, см. в разделе [Использование типов даты и времени](../native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Общие сведения о типах данных даты и времени вы найдете в разделе документации [datetime (Transact-SQL)](/sql/t-sql/data-types/datetime-transact-sql).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Поддержка типов данных для улучшений функций даты и времени ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Содержит сведения о типах ODBC, которые поддерживают типы данных даты-времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Метаданные &#40;ODBC&#41;](../../database-engine/dev-guide/metadata-odbc.md)  
 Описывает сведения, возвращенные в полях дескрипторов параметра реализации (IPD) и строки реализации (IRD), а также метаданные столбца, возвращенные `SQLColumns` и `SQLProcedureColumns`. Также описывает метаданные типов данных, возвращенные `SQLGetTypeInfo`.  
  
 [Преобразования типов данных DateTime &#40;ODBC&#41;](datetime-data-type-conversions-odbc.md)  
 Описывает, как выполнять преобразование между значениями типа datetime и datetimeoffset.  
  
 [Поддержка sql_variant для типов даты и времени](sql-variant-support-for-date-and-time-types.md)  
 Описывает функцию SQL_VARIANT, поддерживающую улучшенные возможности типов данных даты-времени.  
  
 [Изменения в ходе операции копирования для расширенных типов даты и времени &#40;OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Улучшенное поведение типов даты и времени с предыдущими версиями SQL Server &#40;ODBC&#41;](enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Описывает ожидаемое поведение при соединении клиентского приложения, использующего улучшенные возможности типов данных даты-времени со старой версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и при отправке клиентом, скомпилированным с помощью старой версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], команд на сервер, который поддерживает улучшенные возможности по работе с данными в формате даты-времени.  
  
 [Поддержка API-интерфейса ODBC для улучшенных функций даты и времени](odbc-api-support-for-enhanced-date-and-time-features.md)  
 Перечисляет функции ODBC, поддерживающие улучшенные возможности даты и времени.  
  
## <a name="see-also"></a>См. также  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  

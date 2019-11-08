---
title: Улучшения даты и времени (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7cc697c60857f47630dd041762f90f789dd170d5
ms.sourcegitcommit: 856e42f7d5125d094fa84390bc43048808276b57
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2019
ms.locfileid: "73783877"
---
# <a name="date-and-time-improvements-odbc"></a>Улучшения функций даты и времени (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены новые типы данных даты и времени. В этом разделе описаны способы предоставления новых типов в виде расширений в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] собственного клиента. Общие сведения о поддержке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client для новых типов данных даты и времени см. в разделе [улучшения даты и времени](../../relational-databases/native-client/features/date-and-time-improvements.md). Пример, демонстрирующий поддержку даты и времени ODBC, см. в разделе [Использование типов даты и времени](../../relational-databases/native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Дополнительные общие сведения о типах данных даты и времени см. в [разделе &#40;DateTime Transact-&#41;SQL](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>В этом разделе  
 [Поддержка типов данных для улучшений функций даты и времени ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Содержит сведения о типах ODBC, которые поддерживают типы данных даты-времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Метаданные &#40;ODBC&#41;](https://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
 Описывает сведения, возвращаемые в полях дескриптора параметра реализации (IPD) и дескриптора строки реализации (IRD), а также метаданные столбцов, возвращаемые **SQLColumns** и **SQLProcedureColumns**. Также описывает метаданные типа данных, возвращаемые функцией **SQLGetTypeInfo**.  
  
 [Типы данных DateTime — &#40;ODBC&#41;](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-odbc.md)  
 Описывает, как выполнять преобразование между значениями типа datetime и datetimeoffset.  
  
 [Поддержка sql_variant для типов даты и времени](../../relational-databases/native-client-odbc-date-time/sql-variant-support-for-date-and-time-types.md)  
 Описывает функцию SQL_VARIANT, поддерживающую улучшенные возможности типов данных даты-времени.  
  
 [Изменения в ходе операции копирования для расширенных типов &#40;даты и времени OLE DB и ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Улучшенное поведение типов даты и времени с предыдущими &#40;версиями ODBC для SQL Server&#41;](../../relational-databases/native-client-odbc-date-time/enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Описывает ожидаемое поведение при соединении клиентского приложения, использующего улучшенные возможности типов данных даты-времени со старой версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и при отправке клиентом, скомпилированным с помощью старой версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], команд на сервер, который поддерживает улучшенные возможности по работе с данными в формате даты-времени.  
  
 [Поддержка API-интерфейса ODBC для улучшенных функций даты и времени](../../relational-databases/native-client-odbc-date-time/odbc-api-support-for-enhanced-date-and-time-features.md)  
 Перечисляет функции ODBC, поддерживающие улучшенные возможности даты и времени.  
  
## <a name="see-also"></a>См. также раздел  
 [SQL Server Native Client (ODBC)](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  

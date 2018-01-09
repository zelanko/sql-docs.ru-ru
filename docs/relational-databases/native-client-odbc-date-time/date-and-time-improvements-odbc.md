---
title: "Дата и время усовершенствования (ODBC) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client-odbc-date-time
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC]
- ODBC, date/time improvements
ms.assetid: e31d5ca5-2103-498f-954c-1ee93e217186
caps.latest.revision: "27"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 815e877698cef9b672ea29dc10f31dcf2ed9a565
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="date-and-time-improvements-odbc"></a>Дата и время усовершенствования (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  В [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] добавлены новые типы данных даты и времени. В этом разделе описывается, каким образом эти новые типы доступны в виде расширений в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client. Общие сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддержка собственного клиента новые типы даты и времени типов данных, в разделе [даты и времени усовершенствования](../../relational-databases/native-client/features/date-and-time-improvements.md). Пример, демонстрирующий поддержку ODBC даты и времени см. в разделе [использование данных даты и времени типы](../../relational-databases/native-client-odbc-how-to/use-date-and-time-types.md).  
  
 Дополнительные общие сведения о типах данных даты и времени см. в разделе [datetime &#40; Transact-SQL &#41; ](../../t-sql/data-types/datetime-transact-sql.md).  
  
## <a name="in-this-section"></a>в этом разделе  
 [Поддержка типов данных для улучшений функций даты и времени ODBC](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md)  
 Содержит сведения о типах ODBC, которые поддерживают типы данных даты-времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 [Метаданные &#40; ODBC &#41;](http://msdn.microsoft.com/library/99133efc-b1f2-46e9-8203-d90c324a8e4c)  
 Описывает сведения, возвращенные в дескрипторе параметра реализации (IPD) и реализацию поля дескриптора (IRD) строки, а также метаданные столбцов, возвращенных **SQLColumns** и **SQLProcedureColumns**. Также описывает метаданные типов данных, возвращенных **SQLGetTypeInfo**.  
  
 [Преобразование типов данных DateTime &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/datetime-data-type-conversions-odbc.md)  
 Описывает, как выполнять преобразование между значениями типа datetime и datetimeoffset.  
  
 [Поддержка sql_variant для типов даты и времени](../../relational-databases/native-client-odbc-date-time/sql-variant-support-for-date-and-time-types.md)  
 Описывает функцию SQL_VARIANT, поддерживающую улучшенные возможности типов данных даты-времени.  
  
 [Массовое копирование изменения для улучшение типы даты и времени типы &#40; OLE DB и ODBC &#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 Описываются новые возможности даты-времени для поддержки операций массового копирования.  
  
 [Улучшенные даты и времени поведение типов с предыдущих версий SQL Server &#40; ODBC &#41;](../../relational-databases/native-client-odbc-date-time/enhanced-date-and-time-type-behavior-with-previous-sql-server-versions-odbc.md)  
 Описывает ожидаемое поведение при соединении клиентского приложения, использующего улучшенные возможности типов данных даты-времени со старой версией [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], и при отправке клиентом, скомпилированным с помощью старой версии собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], команд на сервер, который поддерживает улучшенные возможности по работе с данными в формате даты-времени.  
  
 [Поддержка API-интерфейса ODBC для улучшенных функций даты и времени](../../relational-databases/native-client-odbc-date-time/odbc-api-support-for-enhanced-date-and-time-features.md)  
 Перечисляет функции ODBC, поддерживающие улучшенные возможности даты и времени.  
  
## <a name="see-also"></a>См. также:  
 [Собственный клиент SQL Server &#40; ODBC &#41;](../../relational-databases/native-client/odbc/sql-server-native-client-odbc.md)  
  
  

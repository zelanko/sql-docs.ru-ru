---
title: SQL Server Native Client (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLNCLI, ODBC
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- data access [SQL Server Native Client], ODBC
- SQL Server Native Client ODBC driver
- ODBC
- SQL Server Native Client, ODBC
- ODBC, about SQL Server Native Client ODBC driver
ms.assetid: 811d5ba3-a2b8-48c0-adbc-8c91f041f458
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 48fc5ccd2973a530010975171a90f35a2f18a7e7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "73760250"
---
# <a name="sql-server-native-client-odbc"></a>Собственный клиент SQL Server (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ODBC — это стандартное определение прикладного программного интерфейса (API), который используется для доступа к данным в реляционных базах данных и базах данных с индексно-последовательным методом доступа (ISAM). 
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает ODBC через драйвер ODBC клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client как один из собственных API для написания приложений на языках C и C++, взаимодействующих с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Программы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], написанные с помощью драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], взаимодействуют с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью вызовов функций на языке C. Специфичные для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии функций ODBC реализованы в драйвере ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер передает инструкции SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и возвращает приложению результаты их выполнения.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] соответствует требованиям спецификации Microsoft Win32 ODBC 3.51. Драйвер поддерживает приложения, написанные с применением более ранних версий ODBC согласно спецификации ODBC 3.51.  
  
## <a name="in-this-section"></a>в этом разделе  
  
-   [Имена источников данных и 64-разрядные операционные системы](../../../relational-databases/native-client/odbc/data-source-names-and-64-bit-operating-systems.md)  
  
-   [Создание драйвера ODBC для собственного клиента SQL Server](../../../relational-databases/native-client/odbc/creating-a-driver-application.md)  
  
-   [Взаимодействие с SQL Server &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [Выполняя запросы &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [Обработка результатов &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-results/processing-results-odbc.md)  
  
-   [Использование курсоров &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [Выполнение транзакций &#40;ODBC&#41;](https://msdn.microsoft.com/library/f431191a-5762-4f0b-85bb-ac99aff29724)  
  
-   [Обработка ошибок и сообщений](../../../relational-databases/native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [Выполнение хранимых процедур](../../../relational-databases/native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [Использование функций каталога](../../../relational-databases/native-client/odbc/using-catalog-functions.md)  
  
-   [Выполнение операций с массовым копированием &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [Управление столбцами text и image](../../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [Создание профилей производительности драйвера ODBC](../../../relational-databases/native-client/odbc/profiling-odbc-driver-performance.md)  
  
-   [Возвращающие табличное значение параметры &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [Улучшения даты и времени &#40;ODBC&#41;](../../../relational-databases/native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [Большие определяемые пользователем типы данных CLR &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)  
  
-   [Поддержка FILESTREAM &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/filestream-support-odbc.md)  
  
-   [Имена участника-службы (SPN) в клиентских соединениях (ODBC)](../../../relational-databases/native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Разреженные столбцы поддерживают &#40;ODBC&#41;](../../../relational-databases/native-client/odbc/sparse-columns-support-odbc.md)  
  
-   [Справочник по SQL Server Native Client &#40;ODBC&#41;](https://msdn.microsoft.com/library/06b7edee-8636-49d9-9b5c-2c710bf4fa2d)  
  
-   [ODBC How-to Topics](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client программирование](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Установка собственного клиента SQL Server](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
  
  

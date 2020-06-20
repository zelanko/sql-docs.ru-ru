---
title: SQL Server Native Client (ODBC) | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 90ab34064ec5114d352b73474afd6791e73f1f3f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85011082"
---
# <a name="sql-server-native-client-odbc"></a>Собственный клиент SQL Server (ODBC)
  ODBC — это стандартное определение прикладного программного интерфейса (API), который используется для доступа к данным в реляционных базах данных и базах данных с индексно-последовательным методом доступа (ISAM). [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддерживает ODBC через драйвер ODBC клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client как один из собственных API для написания приложений на языках C и C++, взаимодействующих с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Программы [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], написанные с помощью драйвера ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], взаимодействуют с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью вызовов функций на языке C. Специфичные для [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] версии функций ODBC реализованы в драйвере ODBC собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Драйвер передает инструкции SQL в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и возвращает приложению результаты их выполнения.  
  
 Драйвер ODBC для собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] соответствует требованиям спецификации Microsoft Win32 ODBC 3.51. Драйвер поддерживает приложения, написанные с применением более ранних версий ODBC согласно спецификации ODBC 3.51.  
  
## <a name="in-this-section"></a>В этом разделе  
  
-   [Имена источников данных и 64-разрядные операционные системы](data-source-names-and-64-bit-operating-systems.md)  
  
-   [Создание драйвера ODBC для собственного клиента SQL Server](creating-a-driver-application.md)  
  
-   [Взаимодействие с SQL Server &#40;ODBC&#41;](../../native-client-odbc-communication/communicating-with-sql-server-odbc.md)  
  
-   [Выполняя запросы &#40;ODBC&#41;](../../native-client-odbc-queries/executing-queries-odbc.md)  
  
-   [Обработка результатов &#40;ODBC&#41;](../../native-client-odbc-results/processing-results-odbc.md)  
  
-   [Использование курсоров &#40;ODBC&#41;](../../native-client-odbc-cursors/using-cursors-odbc.md)  
  
-   [Выполнение транзакций &#40;ODBC&#41;](../../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
-   [Обработка ошибок и сообщений](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
-   [Выполнение хранимых процедур](../../native-client-odbc-stored-procedures/running-stored-procedures.md)  
  
-   [Использование функций каталога](using-catalog-functions.md)  
  
-   [Выполнение операций с массовым копированием &#40;ODBC&#41;](../../native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
-   [Управление столбцами text и image](../../native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
-   [Создание профилей производительности драйвера ODBC](profiling-odbc-driver-performance.md)  
  
-   [Возвращающие табличное значение параметры &#40;ODBC&#41;](../../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)  
  
-   [Улучшения даты и времени &#40;ODBC&#41;](../../native-client-odbc-date-time/date-and-time-improvements-odbc.md)  
  
-   [Большие определяемые пользователем типы данных CLR &#40;ODBC&#41;](large-clr-user-defined-types-odbc.md)  
  
-   [Поддержка FILESTREAM &#40;ODBC&#41;](filestream-support-odbc.md)  
  
-   [Имена участника-службы (SPN) в клиентских соединениях (ODBC)](service-principal-names-spns-in-client-connections-odbc.md)  
  
-   [Разреженные столбцы поддерживают &#40;ODBC&#41;](sparse-columns-support-odbc.md)  
  
-   [Справочник по SQL Server Native Client &#40;ODBC&#41;](../../../database-engine/dev-guide/sql-server-native-client-odbc-reference.md)  
  
-   [ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server Native Client программирование](../sql-server-native-client-programming.md)   
 [Установка собственного клиента SQL Server](../applications/installing-sql-server-native-client.md)  
  
  

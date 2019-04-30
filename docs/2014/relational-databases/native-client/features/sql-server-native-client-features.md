---
title: Компоненты собственного клиента SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], features
ms.assetid: 7bb32865-5afb-41ab-98b4-3fa545ee8953
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 093d40734b88cc370e0c08a8f9a8b86312409e6b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63225563"
---
# <a name="sql-server-native-client-features"></a>Компоненты собственного клиента SQL Server
  Помимо возможностей компонентов доступа к данным WDAC (ранее MDAC), в собственном клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] реализовано множество других функций, позволяющих пользоваться функциональностью [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 [Изменение поведения драйвера ODBC при обработке преобразования символов](odbc-driver-behavior-change-when-handling-character-conversions.md)  
 Описание изменения поведения, реализованного с версии Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 2012.  
  
 [Использование зеркального отображения базы данных](using-database-mirroring.md)  
 Рассматриваются как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client поддерживает использование зеркальных баз данных, который является возможность хранить копию или зеркальную из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных на резервном сервере.  
  
 [Выполнение асинхронных операций](performing-asynchronous-operations.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] асинхронных операций, то есть способности немедленно возвращать управление, не блокируя вызывающий поток.  
  
 [Использование множественных активных результирующих наборов (MARS)](using-multiple-active-result-sets-mars.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] режима MARS. Режим MARS позволяет выполнять и получать несколько результирующих наборов через одно подключение к базе данных.  
  
 [Использование типов данных XML](using-xml-data-types.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типа данных XML (представляющего собой тип данных на основе XML), который можно использовать как тип столбца, переменной, параметра или значения, возвращаемого функцией.  
  
 [Использование определяемых пользователем типов](using-user-defined-types.md)  
 Рассматриваются как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client поддерживает определяемые пользователем типы (UDT), который расширяет систему типов SQL, позволяя сохранять объекты и настраиваемые структуры данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных.  
  
 [Использование типов больших значений](using-large-value-types.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] типов данных больших значений, то есть типов данных больших объектов (LOB).  
  
 [Смена пароля программным способом](changing-passwords-programmatically.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] управления истекшими паролями с возможностью сменить пароль на клиенте без вмешательства администратора.  
  
 [Работа с изоляцией моментального снимка](working-with-snapshot-isolation.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] расширений управления версиями строк, предназначенных для улучшения производительности путем исключения сценариев блокировки модулей чтения или записи.  
  
 [Работа с уведомлениями запросов](working-with-query-notifications.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] уведомления потребителя об изменении набора строк.  
  
 [Выполнение операций массового копирования](performing-bulk-copy-operations.md)  
 Рассматриваются как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client поддерживает операции массового копирования, обеспечивающие передачу больших объемов данных, в который или из которого [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицы или представления.  
  
 [Использование шифрования без проверки](using-encryption-without-validation.md)  
 Обсуждение использования собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] для шифрования данных, передаваемых на сервер, без проверки сертификата.  
  
 [Возвращающие табличные значения параметров &#40;собственный клиент SQL Server&#41;](table-valued-parameters-sql-server-native-client.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] возвращающих табличные значения параметров.  
  
 [Большие определяемые пользователем типы данных CLR](../../clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)  
 Обсуждение поддержки определяемых пользователем типов данных среды CLR.  
  
 [Поддержка FILESTREAM](filestream-support.md)  
 Обсуждаются [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] поддержка Native Client для улучшенной функции FILESTREAM.  
  
 [Поддержка имени субъекта-службы &#40;SPN&#41; в клиентских соединениях](service-principal-name-spn-support-in-client-connections.md)  
 Обсуждение расширенной поддержки имен участника-службы (SPN) для проведения взаимной проверки подлинности по всем протоколам.  
  
 [Поддержка разреженных столбцов в SQL Server Native Client](sparse-columns-support-in-sql-server-native-client.md)  
 Обсуждение поддержки собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] разреженных столбцов.  
  
 [Улучшения функций даты и времени](date-and-time-improvements.md)  
 Обсуждение поддержки новых типов данных даты и времени, добавленной в собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Обнаружение метаданных](metadata-discovery.md)  
 Обсуждение улучшений в механизме обнаружения метаданных, внесенных в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Поддержка UTF-16 в SQL Server Native Client 11.0](utf-16-support-in-sql-server-native-client-11-0.md)  
 Рассматривает изменение поведения, появившееся в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины, а символ `wchar`, записываемый в буфер перед завершающим символом, является старшим символом суррогатной пары, а следующий символ `wchar` является младшим символом суррогатной пары, то клиент Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не добавит в буфер старший символ суррогатной пары.  
  
 [Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server](sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
 Описывается настройка приложения для использования функций высокого уровня доступности и аварийного восстановления, появившихся в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Доступ к диагностическим сведениям в журнале расширенных событий](accessing-diagnostic-information-in-the-extended-events-log.md)  
 Описывает улучшения, реализованные в клиенте [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, и функции отслеживания данных, которые дают доступ к диагностическим данным в кольцевом буфере и журналах XEvents.  
  
 [Поддержка SQL Server Native Client для LocalDB](sql-server-native-client-support-for-localdb.md)  
 Обсуждение поддержки клиентом Native Client [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] улучшенной функции LocalDB.  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../sql-server-native-client-programming.md)   
 [Инструкции по ODBC](../../native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Инструкции по OLE DB](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)   
 [Установка SQL Server Native Client](../applications/installing-sql-server-native-client.md)  
  
  

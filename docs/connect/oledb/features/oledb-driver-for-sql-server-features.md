---
title: Драйвер OLE DB для компонентов SQL Server | Документы Microsoft
description: Драйвер OLE DB для компонентов SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- MDAC [SQL Server]
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], features
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: 5cbc52f29aa0bfc6c60d9f8b7cb47b138c11b561
ms.sourcegitcommit: 354ed9c8fac7014adb0d752518a91d8c86cdce81
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/14/2018
ms.locfileid: "35612359"
---
# <a name="ole-db-driver-for-sql-server-features"></a>Драйвер OLE DB для компонентов SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-asdbmi-md](../../../includes/appliesto-ss-asdb-asdw-pdw-asdbmi-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  Помимо возможностей компонентов доступа Windows (ранее MDAC) данные (WDAC), драйвер OLE DB для SQL Server также реализует множество других возможностей для предоставления [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] функциональные возможности.  
  
## <a name="in-this-section"></a>в этом разделе    
 [Использование зеркального отображения базы данных](../../oledb/features/using-database-mirroring.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает использование зеркальных баз данных, — это возможность сохранять копию или зеркальную из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных на резервном сервере.  
  
 [Выполнение асинхронных операций](../../oledb/features/performing-asynchronous-operations.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает асинхронные операции, который может возвращаться немедленно без блокировки в вызывающем потоке.  
  
 [Использование множественных активных результирующих наборов (MARS)](../../oledb/features/using-multiple-active-result-sets-mars.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает несколько активных результирующих наборов (MARS). Режим MARS позволяет выполнять и получать несколько результирующих наборов через одно подключение к базе данных.  
  
 [Использование типов данных XML](../../oledb/features/using-xml-data-types.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает тип данных XML, который является типом данных XML, которое может использоваться как тип столбца, тип переменной, тип параметра или тип возвращаемого значения функции.  
  
 [Использование определяемых пользователем типов](../../oledb/features/using-user-defined-types.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает определяемые пользователем типы (UDT), который расширяет систему типов SQL, позволяя хранить объекты и пользовательские структуры данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] базы данных.  
  
 [Использование типов больших значений](../../oledb/features/using-large-value-types.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает типы данных больших значений, которые являются типы данных больших объектов (LOB).  
  
 [Смена пароля программным способом](../../oledb/features/changing-passwords-programmatically.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает управления истекшими паролями, чтобы пароли теперь могут быть изменены на клиенте без вмешательства администратора.  
  
 [Работа с изоляцией моментального снимка](../../oledb/features/working-with-snapshot-isolation.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает усовершенствование управления версиями строк, увеличивает производительность базы данных путем исключения сценариев блокировки модулей чтения или записи.  
  
 [Работа с уведомлениями запросов](../../oledb/features/working-with-query-notifications.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает уведомление потребителей об изменении набора строк.  
  
 [Выполнение операций массового копирования](../../oledb/features/performing-bulk-copy-operations.md)  
 Описывает, как драйвер OLE DB для SQL Server поддерживает операции массового копирования, обеспечивающие передачу больших объемов данных в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] таблицу или представление.  
  
 [Использование шифрования без проверки](../../oledb/features/using-encryption-without-validation.md)  
 Описывает, как использовать драйвер OLE DB для SQL Server для шифрования данных, отправляемых на сервер без проверки сертификата.  
  
 [Возвращающие табличные значения параметров &#40;драйвер OLE DB для SQL Server&#41;](../../oledb/features/table-valued-parameters-oledb-driver-for-sql-server.md)  
 Описывает драйвер OLE DB для SQL Server поддержку табличное значение параметров.  
  
 [Большие определяемые пользователем типы данных CLR](../../oledb/features/large-clr-user-defined-types.md)  
 Обсуждение поддержки определяемых пользователем типов данных среды CLR.  
  
 [Поддержка FILESTREAM](../../oledb/features/filestream-support.md)  
 Описывает драйвер OLE DB для SQL Server поддержку улучшенной функции FILESTREAM.  
  
 [Имя участника-службы &#40;имени участника-службы&#41; поддержка в клиентских соединениях](../../oledb/features/service-principal-name-spn-support-in-client-connections.md)  
 Обсуждение расширенной поддержки имен участника-службы (SPN) для проведения взаимной проверки подлинности по всем протоколам.  
  
 [Поддержка разреженных столбцов в драйвере OLE DB для SQL Server](../../oledb/features/sparse-columns-support-in-oledb-driver-for-sql-server.md)  
 Содержит описание драйвер OLE DB для SQL Server, поддержка разреженных столбцов.  
  
 [Улучшения функций даты и времени](../../oledb/features/date-and-time-improvements.md)  
 Обсуждение поддержки добавлены драйвер OLE DB для SQL Server для типов данных даты и времени.  
  
 [Обнаружение метаданных](../../oledb/features/metadata-discovery.md)  
 Обсуждение улучшений в механизме обнаружения метаданных, внесенных в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Поддержка UTF-16 в драйвере OLE DB для SQL Server](../../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  
 Рассматривает изменение поведения, появившееся в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]. Если при привязке результата столбца или выходного параметра указывается буфер фиксированной длины и **wchar** символ, записываемый в буфер перед завершающим символом, является старшим суррогатной пары, а также если следующего **wchar** символ является младшим символом-заместителем кодовая точка, драйвер OLE DB для SQL Server не добавит в буфер старший символ-заместитель кодовую точку.  
  
 [Поддержка высокого уровня доступности и аварийного восстановления в драйвере OLE DB для SQL Server](../../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  
 Описывает, как можно настроить приложение, чтобы воспользоваться преимуществами высокого уровня доступности, аварийного восстановления, появившихся в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Доступ к диагностическим сведениям в журнале расширенных событий](../../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
 Описание усовершенствований драйвер OLE DB для SQL Server и данные трассировки, который предоставляет доступ к диагностическим сведениям в в кольцевом буфере и журналах XEvents.  
  
 [Поддержка драйвера OLE DB для SQL Server в LocalDB](../../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  
 Описывает драйвер OLE DB для SQL Server поддержку функции LocalDB.  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server](../../oledb/oledb-driver-for-sql-server.md)      
 [Разделы руководства по OLE DB](../../oledb/ole-db-how-to/ole-db-how-to-topics.md)   
 [Установка драйвера OLE DB для SQL Server](../../oledb/applications/installing-oledb-driver-for-sql-server.md)  
  
  

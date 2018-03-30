---
title: Драйвер OLE DB для SQL Server | Документы Microsoft
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
description: ''
ms.custom: ''
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: article
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 89e66fe2c61ae17a43e2a58071ba04374f33ea04
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2018
---
# <a name="ole-db-driver-for-sql-server"></a>Драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

MSOLEDBSQL или драйвер OLE DB для SQL Server — это термин, который взаимозаменяемо использовался обращайтесь к драйвер OLE DB для SQL Server.

## <a name="different-incarnations-of-ole-db-drivers"></a>Другой деятельности драйверы OLE DB

Существует три различных версиях поставщиков Microsoft OLE DB для SQL Server.


### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Поставщик Microsoft OLE DB для SQL Server (SQLOLEDB)

[Поставщик Microsoft OLE DB для SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB), по-прежнему поставляется как часть [компоненты доступа к данным Windows](https://msdn.microsoft.com/en-us/library/ms692897.aspx). Не рекомендуется использовать этот драйвер для разработки новых приложений.


### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)

Начиная с SQL Server 2005 [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) включает интерфейс поставщика OLE DB (SQLNCLI) и поставщика OLE DB, поставляемую с SQL Server 2005 через 2017 г. SQL Server.

Это было [устаревшие в 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) и не рекомендуется использовать этот драйвер для разработки новых приложений.


### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL)

OLE DB не [было объявлено в 2017 г undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/). Новый выпуск плановой было объявлено для 2018.

Новый поставщик OLE DB, называется драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL). Новый поставщик будет добавлено в последние функции сервера Забегая вперед.

Сведения о драйвер OLE DB для компонентов SQL Server:

-   [Драйвер OLE DB для SQL Server Support for LocalDB](../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  

-   [Обнаружение метаданных](../oledb/features/metadata-discovery.md)  

-   [Поддержка UTF-16 в драйвер OLE DB для SQL Server](../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  

-   [Драйвер OLE DB для SQL Server поддержку высокого уровня доступности и аварийного восстановления](../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  

-   [Доступ к диагностическим сведениям в журнале расширенных событий](../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

## <a name="see-also"></a>См. также:  
[Установите драйвер OLE DB для SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)  
 [Драйвер OLE DB для компонентов SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )  

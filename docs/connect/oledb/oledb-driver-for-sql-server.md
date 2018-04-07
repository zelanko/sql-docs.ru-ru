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
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 5f009cf311c1eb395915e017bf202abea5ae5290
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="ole-db-driver-for-sql-server"></a>Драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

MSOLEDBSQL или драйвер OLE DB для SQL Server — это термин, который взаимозаменяемыми обращайтесь к драйвер OLE DB для SQL Server.

## <a name="different-generations-of-ole-db-drivers"></a>Разных поколений драйверы OLE DB

Существует три поколения различных поставщиков Microsoft OLE DB для SQL Server.

### <a name="1-microsoft-ole-db-provider-for-sql-server-sqloledb"></a>1. Поставщик Microsoft OLE DB для SQL Server (SQLOLEDB)
[Поставщик Microsoft OLE DB для SQL Server](../../ado/guide/appendixes/microsoft-ole-db-provider-for-sql-server.md) (SQLOLEDB), по-прежнему поставляется как часть [компоненты доступа к данным Windows](https://msdn.microsoft.com/en-us/library/ms692897.aspx). Больше не поддерживается и не рекомендуется использовать этот драйвер для разработки новых приложений. 


### <a name="2-sql-server-native-client-snac"></a>2. SQL Server Native Client (SNAC)
Начиная с версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], [SQL Server Native Client (SNAC)](../../relational-databases/native-client/sql-server-native-client.md) включает интерфейс поставщика OLE DB (SQLNCLI) и поставщика OLE DB, которая поставлялась с [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] через [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].

Это было [устаревшие в 2011](https://blogs.msdn.microsoft.com/sqlnativeclient/2011/08/29/microsoft-is-aligning-with-odbc-for-native-relational-data-access/) и не рекомендуется использовать этот драйвер для разработки новых приложений. Дополнительные сведения о SNAC жизненный цикл и программ для загрузки см. [жизненного цикла SNAC описано](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).

### <a name="3-microsoft-ole-db-driver-for-sql-server-msoledbsql"></a>3. Драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL)
OLE DB не [undeprecated](https://blogs.msdn.microsoft.com/sqlnativeclient/2017/10/06/announcing-the-new-release-of-ole-db-driver-for-sql-server/) выпущена в 2018 и могут быть загружены [здесь](https://go.microsoft.com/fwlink/?linkid=871294).

Новый поставщик OLE DB, называется драйвер Microsoft OLE DB для SQL Server (MSOLEDBSQL). Новый поставщик будет добавлено в последние функции сервера Забегая вперед.

> [!NOTE]
> Чтобы использовать новый Microsoft OLE DB драйвер для SQL Server в существующих приложениях, следует запланировать для преобразования строки подключения из SQLOLEDB и SQLNCLI, MSOLEDBSQL.   

Сведения о драйвер OLE DB для компонентов SQL Server:

-   [Поддержка драйвера OLE DB для SQL Server в LocalDB](../oledb/features/oledb-driver-for-sql-server-support-for-localdb.md)  

-   [Обнаружение метаданных](../oledb/features/metadata-discovery.md)  

-   [Поддержка UTF-16 в драйвере OLE DB для SQL Server](../oledb/features/utf-16-support-in-oledb-driver-for-sql-server.md)  

-   [Поддержка высокого уровня доступности и аварийного восстановления в драйвере OLE DB для SQL Server](../oledb/features/oledb-driver-for-sql-server-support-for-high-availability-disaster-recovery.md)  

-   [Доступ к диагностическим сведениям в журнале расширенных событий](../oledb/features/accessing-diagnostic-information-in-the-extended-events-log.md)  

## <a name="see-also"></a>См. также:  
[Установите драйвер OLE DB для SQL Server](../oledb/applications/installing-oledb-driver-for-sql-server.md)     
[Возможности драйвера OLE DB для SQL Server](../oledb/features/oledb-driver-for-sql-server-features.md )     

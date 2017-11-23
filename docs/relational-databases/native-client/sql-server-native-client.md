---
title: "Собственный клиент SQL Server | Документы Microsoft"
ms.date: 04/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology: docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4d4fe39-0090-42a7-8405-6378370d11cb
caps.latest.revision: "43"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 2efcd738e4f5e1047f5d265ea063e90a7cdb8de8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="sql-server-native-client"></a>собственный клиент SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

SNAC или собственный клиент SQL Server — это термин, который взаимозаменяемо использовался для обращения к драйверам ODBC и OLE DB для SQL Server. 

**Дополнительные сведения и загрузить SNAC или драйверов ODBC, посетите [жизненного цикла SNAC описано](https://blogs.msdn.microsoft.com/sqlreleaseservices/snac-lifecycle-explained/).**

Дополнительные сведения о драйвер ODBC для SQL Server см. в разделе [драйвер ODBC для SQL Server в Windows](https://msdn.microsoft.com/library/jj730314(v=sql.110).aspx).  См. также [Общие сведения о новых драйверов Microsoft ODBC для SQL Server](https://blogs.msdn.microsoft.com/sqlnativeclient/2013/01/23/introducing-the-new-microsoft-odbc-drivers-for-sql-server/), и [ODBC Driver 13.1 for SQL Server выпуска](https://blogs.technet.microsoft.com/dataplatforminsider/2016/08/03/odbc-driver-13-1-for-sql-server-released/).  
  
 Сведения о [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] функции собственного клиента, выпущенная вместе с [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], последней доступной версии собственного клиента SQL Server: 
  
-   [Поддержка SQL Server Native Client для LocalDB](../../relational-databases/native-client/features/sql-server-native-client-support-for-localdb.md)  
  
-   [Обнаружение метаданных](../../relational-databases/native-client/features/metadata-discovery.md)  
  
-   [Поддержка UTF-16 в SQL Server Native Client 11.0](../../relational-databases/native-client/features/utf-16-support-in-sql-server-native-client-11-0.md)  
  
-   [Поддержка высокого уровня доступности и аварийного восстановления собственного клиента SQL Server](../../relational-databases/native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)  
  
-   [Доступ к диагностическим сведениям в журнале расширенных событий](../../relational-databases/native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)  
  
ODBC в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client поддерживает три функции, которые были добавлены в стандарт ODBC в Windows 7 SDK:  
  
-   Асинхронное выполнение операций, связанных с соединением. Дополнительные сведения см. в разделе [Асинхронное выполнение](http://go.microsoft.com/fwlink/?LinkID=191493).  
  
-   Возможность расширения типа данных C. Дополнительные сведения о типах данных см. в разделе [Типы данных C в ODBC](http://go.microsoft.com/fwlink/?LinkID=191495).  
  
     Для поддержки этой возможности в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client может возвращать SQLGetDescField **SQL_C_SS_TIME2** (для **время** типов) или **SQL_C_SS_TIMESTAMPOFFSET** (для **datetimeoffset**) вместо **SQL_C_BINARY**, если приложение использует ODBC 3.8. Дополнительные сведения см. в разделе [поддержка типов данных для ODBC Дата и время улучшениях](../../relational-databases/native-client-odbc-date-time/data-type-support-for-odbc-date-and-time-improvements.md).  
  
-   Многократный вызов метода **SQLGetData** с небольшим буфером для получения значения параметра большого объема. Дополнительные сведения см. в разделе [Получение выходных параметров с помощью метода SQLGetData](http://go.microsoft.com/fwlink/?LinkID=191494).  
  
 В следующих разделах описываются изменения поведения собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].  
  
-   При вызове метода **ICommandWithParameters::SetParameterInfo**значение, передаваемое в параметре *pwszName* , должно быть допустимым идентификатором. Дополнительные сведения см. в разделе [ICommandWithParameters](../../relational-databases/native-client-ole-db-interfaces/icommandwithparameters.md).  
  
-   **SQLDescribeParam** постоянно будет возвращать значение, соответствующие требованиям спецификации ODBC. Дополнительные сведения см. в разделе [SQLDescribeParam](../../relational-databases/native-client-odbc-api/sqldescribeparam.md).  
  
-   [Изменение поведения драйвера ODBC при обработке преобразования символов](../../relational-databases/native-client/features/odbc-driver-behavior-change-when-handling-character-conversions.md)  
  
## <a name="see-also"></a>См. также:  
[Установить собственный клиент SQL Server](../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 [Компоненты SQL Server Native Client](../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  

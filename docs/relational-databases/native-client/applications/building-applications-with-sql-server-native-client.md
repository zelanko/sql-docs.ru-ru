---
title: "Построение приложений с помощью собственного клиента SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client|applications
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], building applications
- SQLNCLI, building applications
- applications [SQL Server Native Client]
- SQL Server Native Client, building applications
ms.assetid: 254a2b48-f0e3-43b5-a48d-3d666c2a779f
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 834eb3d75a973b46255d690a504c2a3d17a68c48
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="building-applications-with-sql-server-native-client"></a>Построение приложений с использованием собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  При разработке приложения, использующего библиотеку собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], следует учитывать ряд проблем. В этом разделе обсуждаются многие из этих проблем, в том числе переход от компонентов MDAC к собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и использование файлов заголовков и библиотек собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также приведены общие сведения о различных строках соединения, которые можно использовать с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>В этом разделе  
 [Установка собственного клиента SQL Server](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 Обсуждаются способ установки собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], местоположения установки различных компонентов, а также способ удаления собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Компоненты собственного клиента SQL Server](../../../relational-databases/native-client/applications/components-of-sql-server-native-client.md)  
 Обсуждаются компоненты, входящие в состав собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в том числе файлы библиотек, ресурсов, справки и заголовков.  
  
 [С помощью ключевых слов строки подключения с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
 Обсуждаются различные типы строк соединения, которые можно использовать для соединения с базой данных через собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [С помощью заголовка собственного клиента SQL Server и файлы библиотек](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md)  
 Обсуждается использование файлов заголовков и библиотек собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в приложении.  
  
 [Обновление приложения для собственного клиента SQL Server с компонентами MDAC](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)  
 Обсуждаются отличия собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] от компонентов MDAC и проблемы, которые следует принимать во внимание при переходе с компонентов MDAC на собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Обновление приложения от собственного клиента SQL Server 2005](../../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md)  
 Обсуждаются вопросы, которые необходимо учитывать при обновлении собственного клиента [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] до собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Использование ADO с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md)  
 Обсуждается использование собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] технологией ADO для доступа к СУБД [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и ее функциям.  
  
 [Политики поддержки для собственного клиента SQL Server](../../../relational-databases/native-client/applications/support-policies-for-sql-server-native-client.md)  
 Объясняет, как могут использоваться различные компоненты доступа к данным с разными версиями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 [Соединение с базой данных SQL Windows Azure с помощью SQL Server Native Client](../../../relational-databases/native-client/applications/connecting-to-a-windows-azure-sql-database-using-sql-server-native-client.md)  
 Содержит сведения о соединении с базой данных [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] через [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>См. также:  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Инструкции по ODBC](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Разделы руководства по OLE DB](../../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  

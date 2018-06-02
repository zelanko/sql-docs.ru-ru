---
title: Построение приложений с помощью собственного клиента SQL Server | Документы Microsoft
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client|applications
ms.reviewer: ''
ms.suite: sql
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], building applications
- SQLNCLI, building applications
- applications [SQL Server Native Client]
- SQL Server Native Client, building applications
ms.assetid: 254a2b48-f0e3-43b5-a48d-3d666c2a779f
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 7f05a62a79bb0773563d29a053f3221b10f6d931
ms.sourcegitcommit: 2d93cd115f52bf3eff3069f28ea866232b4f9f9e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/01/2018
ms.locfileid: "34708242"
---
# <a name="building-applications-with-sql-server-native-client"></a>Построение приложений с использованием собственного клиента SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  При разработке приложения, использующего библиотеку собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], следует учитывать ряд проблем. В этом разделе обсуждаются многие из этих проблем, в том числе переход от компонентов MDAC к собственному клиенту [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и использование файлов заголовков и библиотек собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], а также приведены общие сведения о различных строках соединения, которые можно использовать с собственным клиентом [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="in-this-section"></a>в этом разделе  
 [Установка SQL Server Native Client](../../../relational-databases/native-client/applications/installing-sql-server-native-client.md)  
 Обсуждаются способ установки собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], местоположения установки различных компонентов, а также способ удаления собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Компоненты SQL Server Native Client](../../../relational-databases/native-client/applications/components-of-sql-server-native-client.md)  
 Обсуждаются компоненты, входящие в состав собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], в том числе файлы библиотек, ресурсов, справки и заголовков.  
  
 [Использование ключевых слов строки подключения с собственным клиентом SQL Server](../../../relational-databases/native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)  
 Обсуждаются различные типы строк соединения, которые можно использовать для соединения с базой данных через собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Использование файлов заголовков и библиотек SQL Server Native Client](../../../relational-databases/native-client/applications/using-the-sql-server-native-client-header-and-library-files.md)  
 Обсуждается использование файлов заголовков и библиотек собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в приложении.  
  
 [Обновление приложения с переходом от компонентов MDAC к SQL Server Native Client](../../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md)  
 Обсуждаются отличия собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] от компонентов MDAC и проблемы, которые следует принимать во внимание при переходе с компонентов MDAC на собственный клиент [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 [Обновление приложения с переходом от SQL Server 2005 Native Client](../../../relational-databases/native-client/applications/updating-an-application-from-sql-server-2005-native-client.md)  
 Обсуждаются вопросы, которые необходимо учитывать при обновлении собственного клиента [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] до собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].  
  
 [Использование ADO с SQL Server Native Client](../../../relational-databases/native-client/applications/using-ado-with-sql-server-native-client.md)  
 Обсуждается использование собственного клиента [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] технологией ADO для доступа к СУБД [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и ее функциям.  
  
 [Политики поддержки SQL Server Native Client](../../../relational-databases/native-client/applications/support-policies-for-sql-server-native-client.md)  
 Объясняет, как могут использоваться различные компоненты доступа к данным с разными версиями [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
 [Соединение с базой данных SQL Windows Azure с помощью SQL Server Native Client](../../../relational-databases/native-client/applications/connecting-to-a-windows-azure-sql-database-using-sql-server-native-client.md)  
 Содержит сведения о соединении с базой данных [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] через [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Инструкции по ODBC](../../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Инструкции по OLE DB](../../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  

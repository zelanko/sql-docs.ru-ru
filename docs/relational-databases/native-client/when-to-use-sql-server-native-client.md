---
title: "Когда следует использовать собственный клиент SQL Server | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: native-client
ms.reviewer: 
ms.suite: sql
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, about SQL Server Native Client ODBC driver
- SQLNCLI, about SQL Server Native Client
- data access [SQL Server Native Client], about SQL Server Native Client
ms.assetid: 08f18b36-209d-4cf7-9623-ebc61859a91d
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 5244bd7ed81e7aeaf11ef63c1a65c28f4094004c
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2018
---
# <a name="when-to-use-sql-server-native-client"></a>Когда использовать собственный клиент SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — одна из технологий для доступа к данным в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Обсуждение технологий различных доступа к данным см. в разделе [схема технологий доступа к данным](http://go.microsoft.com/fwlink/?LinkID=179186)  
  
 В принятии решения о необходимости использования в качестве технологии доступа к данным собственного клиента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] необходимо принимать во внимание ряд факторов.  
  
 Если используется язык программирования с управляемым кодом, например Microsoft Visual C# или Visual Basic, и необходимо обращаться к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то для новых приложений следует пользоваться поставщиком данных .NET Framework для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который является частью платформы .NET Framework.  
  
 Если разрабатывается приложение на основе COM и необходим доступ к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует использовать собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если доступ к новым возможностям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется, то можно продолжать использовать компоненты WDAC.  
  
 Для существующих приложений OLE DB и ODBC самый важный вопрос — необходим ли доступ к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имеется отлаженное приложение, не требующее новых возможностей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то можно продолжать использование компонентов WDAC. Но если требуется получить доступ к этим новым возможностям, таких как [тип данных xml](../../t-sql/xml/xml-transact-sql.md), следует использовать [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client.  
  
 Собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и MDAC поддерживают уровень изоляции транзакций read committed при использовании управления версиями строк, однако изоляцию транзакций моментальных снимков поддерживает только собственный клиент [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. С точки зрения программирования уровень изоляции транзакции READ COMMITTED с управлением версиями строк — то же самое, что и транзакция READ COMMITTED.  
  
 Дополнительные сведения о различиях между [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client и компонентами MDAC см. в разделе [обновление приложения для собственного клиента SQL Server с компонентами MDAC](../../relational-databases/native-client/applications/updating-an-application-to-sql-server-native-client-from-mdac.md).  
  
## <a name="see-also"></a>См. также  
 [Программирование собственного клиента SQL Server](../../relational-databases/native-client/sql-server-native-client-programming.md)   
 [Инструкции по ODBC](../../relational-databases/native-client-odbc-how-to/odbc-how-to-topics.md)   
 [Разделы руководства по OLE DB](../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  

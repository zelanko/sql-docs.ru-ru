---
title: Когда следует использовать драйвер OLE DB для SQL Server | Документы Microsoft
description: Когда следует использовать драйвер OLE DB для SQL Server
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: oledb
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: 361a13bd249bef726e202fc8fef69fb48d88b746
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2018
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Когда следует использовать драйвер OLE DB для SQL Server
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Драйвер OLE DB для SQL Server — одна из технологий, можно использовать для доступа к данным в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  Обсуждение технологий различных доступа к данным см. в разделе [схема технологий доступа к данным](http://go.microsoft.com/fwlink/?LinkID=179186)  
  
 При определении, следует ли использовать драйвер OLE DB для SQL Server в качестве технологии доступа к данным приложения, следует несколько факторов.  
  
 Если используется язык программирования с управляемым кодом, например Microsoft Visual C# или Visual Basic, и необходимо обращаться к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то для новых приложений следует пользоваться поставщиком данных .NET Framework для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который является частью платформы .NET Framework.  
  
 Если разрабатывается приложение на основе COM и необходим доступ к новым функциям в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует использовать драйвер OLE DB для SQL Server. Если доступ к новым возможностям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется, то можно продолжать использовать компоненты WDAC.  
  
 Для существующих приложений OLE DB, наиболее важным вопросом является необходимость доступа к новым возможностям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имеется отлаженное приложение, не требующее новых возможностей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то можно продолжать использование компонентов WDAC. Но если требуется получить доступ к этим новым возможностям, таких как [тип данных xml](../../t-sql/xml/xml-transact-sql.md), следует использовать драйвер OLE DB для SQL Server.  
  
 Оба драйвер OLE DB для SQL Server и MDAC поддерживают изоляции транзакций read committed с использованием управления версиями строк, но только драйвер OLE DB для изоляции транзакций моментальных снимков SQL Server поддерживает. С точки зрения программирования уровень изоляции транзакции READ COMMITTED с управлением версиями строк — то же самое, что и транзакция READ COMMITTED.  
  
 Сведения о различиях между драйвер OLE DB для SQL Server и компоненты MDAC см. в разделе [обновление приложения для драйвера OLE DB для SQL Server с компонентами MDAC](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>См. также  
 [Драйвер OLE DB для SQL Server программирования](../oledb/oledb-driver-for-sql-server-programming.md)     
 [Разделы руководства по OLE DB](../oledb/ole-db-how-to/ole-db-how-to-topics.md)  
  
  

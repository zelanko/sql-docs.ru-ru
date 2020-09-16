---
title: Сценарии использования OLE DB Driver
description: Узнайте, когда следует использовать OLE DB Driver for SQL Server, и ознакомьтесь с основными понятиями доступа к данным, отличающими этот драйвер от других драйверов.
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server
- MSOLEDBSQL, about OLE DB Driver for SQL Server
- data access [OLE DB Driver for SQL Server], about OLE DB Driver for SQL Server
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bd5237556ec0bbe1bf4101cb5adde9734088217c
ms.sourcegitcommit: c95f3ef5734dec753de09e07752a5d15884125e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/25/2020
ms.locfileid: "88860180"
---
# <a name="when-to-use-ole-db-driver-for-sql-server"></a>Когда использовать драйвер OLE DB для SQL Server
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]

[!INCLUDE[Driver_OLEDB_Download](../../includes/driver_oledb_download.md)]

  OLE DB Driver for SQL Server — это одна из технологий для доступа к данным в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Обсуждение других технологий доступа к данным см. в разделе [Схема технологий доступа к данным](https://go.microsoft.com/fwlink/?LinkID=179186).  
  
 В принятии решения о необходимости использования в качестве технологии доступа к данным драйвера OLE DB для SQL Server необходимо принимать во внимание ряд факторов.  
  
 Если используется язык программирования с управляемым кодом, например Microsoft Visual C# или Visual Basic, и необходимо обращаться к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то для новых приложений следует пользоваться поставщиком данных .NET Framework для [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], который является частью платформы .NET Framework.  
  
 Если разрабатывается приложение на основе COM и необходим доступ к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует использовать драйвер OLE DB для SQL Server. Если доступ к новым возможностям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не требуется, то можно продолжать использовать компоненты WDAC.  
  
 Для существующих приложений OLE DB самый важный вопрос — необходим ли доступ к новым функциям [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Если имеется отлаженное приложение, не требующее новых возможностей [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], то можно продолжать использование компонентов WDAC. Но если требуется доступ к новым возможностям, например к новому [типу данных xml](../../t-sql/xml/xml-transact-sql.md), то необходимо использовать драйвер OLE DB для SQL Server.  
  
 OLE DB Driver for SQL Server и MDAC поддерживают изоляцию транзакций уровня read-committed через управление версиями строк, но только OLE DB Driver for SQL Server поддерживает изоляцию транзакций уровня моментальных снимков. С точки зрения программирования уровень изоляции транзакции READ COMMITTED с управлением версиями строк — то же самое, что и транзакция READ COMMITTED.  
  
 Сведения о различиях между драйверами OLE DB Driver for SQL Server и Windows DAC см. в статье [Обновление приложения с переходом от MDAC на драйвер OLE DB для SQL Server](../oledb/applications/updating-an-application-to-oledb-driver-for-sql-server-from-mdac.md).  
  
## <a name="see-also"></a>См. также:  
 [Драйвер OLE DB для SQL Server](oledb-driver-for-sql-server.md)  
 [Инструкции по OLE DB](ole-db-how-to/ole-db-how-to-topics.md)  
  
  

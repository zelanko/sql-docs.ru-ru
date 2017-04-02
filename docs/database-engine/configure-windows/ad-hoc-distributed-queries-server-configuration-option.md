---
title: "Параметр конфигурации сервера &#171;ad hoc distributed queries&#187; | Microsoft Docs"
ms.custom: ""
ms.date: "03/02/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "функция OPENROWSET, параметр ad hoc distributed queries"
  - "Ad Hoc Distributed Queries, параметр"
  - "нерегламентированные распределенные запросы"
  - "7415 (ошибка в компоненте Database Engine)"
  - "функция OPENDATASOURCE, параметр ad hoc distributed queries"
  - "нерегламентированный доступ"
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
caps.latest.revision: 29
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 29
---
# Параметр конфигурации сервера &#171;ad hoc distributed queries&#187;
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не разрешает нерегламентированные распределенные запросы, использующие операторы OPENROWSET и OPENDATASOURCE. Если этот параметр равен 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] допускает выполнение нерегламентированных распределенных запросов. Если этот параметр не задан или равен 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не разрешает нерегламентированный доступ.  
  
 В нерегламентированных распределенных запросах с помощью функций OPENROWSET и OPENDATASOURCE осуществляется подключение к удаленным источникам данных, использующим OLE DB. Функции OPENROWSET и OPENDATASOURCE должны использоваться с теми источниками данных OLE DB, обращения к которым происходят нечасто. Для источников данных, к которым обращение производится более чем несколько раз, определите связанный сервер.  
  
> [!IMPORTANT]  
>  Разрешение использования нерегламентированных имен означает, что любой пользователь, прошедший проверку подлинности при входе в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , будет иметь доступ к поставщику. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует включить эту функцию для поставщиков, любой локальный доступ к которым не представляет опасности.  
  
## Замечания  
 Попытка установки нерегламентированного соединения без включенной функции **Ad Hoc Distributed Queries** приведет к ошибке: сообщение 7415, уровень 16, состояние 1, строка 1.  
  
 Нерегламентированный доступ к поставщику OLE DB «Microsoft.ACE.OLEDB.12.0» запрещен. К данному поставщику доступ необходимо производить через связанный сервер.  
  
## Примеры  
 Следующий пример включает распределенные нерегламентированные запросы и выполняет запрос к серверу `Seattle1` с использованием функции `OPENROWSET`.  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;
GO 
sp_configure 'Ad Hoc Distributed Queries', 1;  
RECONFIGURE;  
GO  
  
SELECT a.*  
FROM OPENROWSET('SQLNCLI', 'Server=Seattle1;Trusted_Connection=yes;',  
     'SELECT GroupName, Name, DepartmentID  
      FROM AdventureWorks2012.HumanResources.Department  
      ORDER BY GroupName, Name') AS a;  
GO  
```  
  
## См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [OPENDATASOURCE (Transact-SQL)](../../t-sql/functions/opendatasource-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
  
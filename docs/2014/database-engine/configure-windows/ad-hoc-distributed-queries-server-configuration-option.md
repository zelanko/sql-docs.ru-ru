---
title: Параметр конфигурации сервера "ad hoc distributed queries" | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: d172024326dd3b5728fa5aa498a77551403bf9b1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36188531"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a>Параметр конфигурации сервера «ad hoc distributed queries»
  По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не разрешает нерегламентированные распределенные запросы, использующие операторы OPENROWSET и OPENDATASOURCE. Если этот параметр равен 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] допускает выполнение нерегламентированных распределенных запросов. Если этот параметр не задан или равен 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не разрешает нерегламентированный доступ.  
  
 В нерегламентированных распределенных запросах с помощью функций OPENROWSET и OPENDATASOURCE осуществляется подключение к удаленным источникам данных, использующим OLE DB. Функции OPENROWSET и OPENDATASOURCE должны использоваться с теми источниками данных OLE DB, обращения к которым происходят нечасто. Для источников данных, к которым обращение производится более чем несколько раз, определите связанный сервер.  
  
> [!IMPORTANT]  
>  Разрешение использования нерегламентированных имен означает, что любой пользователь, прошедший проверку подлинности при входе в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , будет иметь доступ к поставщику. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует включить эту функцию для поставщиков, любой локальный доступ к которым не представляет опасности.  
  
## <a name="remarks"></a>Примечания  
 Попытка установки нерегламентированного соединения без включенной функции **Ad Hoc Distributed Queries** приведет к ошибке: сообщение 7415, уровень 16, состояние 1, строка 1.  
  
 Нерегламентированный доступ к поставщику OLE DB «Microsoft.ACE.OLEDB.12.0» запрещен. К данному поставщику доступ необходимо производить через связанный сервер.  
  
## <a name="examples"></a>Примеры  
 Следующий пример включает распределенные нерегламентированные запросы и выполняет запрос к серверу `Seattle1` с использованием функции `OPENROWSET` .  
  
```  
sp_configure 'show advanced options', 1;  
RECONFIGURE;  
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
  
## <a name="see-also"></a>См. также  
 [Параметры конфигурации сервера (SQL Server)](server-configuration-options-sql-server.md)   
 [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [OPENROWSET (Transact-SQL)](/sql/t-sql/functions/openrowset-transact-sql)   
 [OPENDATASOURCE (Transact-SQL)](/sql/t-sql/functions/opendatasource-transact-sql)   
 [sp_addlinkedserver (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
  

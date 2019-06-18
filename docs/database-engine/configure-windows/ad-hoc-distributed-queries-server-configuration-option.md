---
title: Параметр конфигурации сервера "ad hoc distributed queries" | Документы Майкрософт
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- OPENROWSET function, ad hoc distributed queries option
- Ad Hoc Distributed Queries option
- ad hoc distributed queries
- 7415 (Database Engine Error)
- OPENDATASOURCE function, ad hoc distributed queries option
- ad hoc access
ms.assetid: 5b982015-e196-44c3-83b8-275fb9d769b2
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: e60261790ce1597c9968fb9c6c3c15403f71a93c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "66786948"
---
# <a name="ad-hoc-distributed-queries-server-configuration-option"></a>Параметр конфигурации сервера «ad hoc distributed queries»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  По умолчанию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не разрешает нерегламентированные распределенные запросы, использующие операторы OPENROWSET и OPENDATASOURCE. Если этот параметр равен 1, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] допускает выполнение нерегламентированных распределенных запросов. Если этот параметр не задан или равен 0, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не разрешает нерегламентированный доступ.  
  
 В нерегламентированных распределенных запросах с помощью функций OPENROWSET и OPENDATASOURCE осуществляется подключение к удаленным источникам данных, использующим OLE DB. Функции OPENROWSET и OPENDATASOURCE должны использоваться с теми источниками данных OLE DB, обращения к которым происходят нечасто. Для источников данных, к которым обращение производится более чем несколько раз, определите связанный сервер.  
  
> [!IMPORTANT]  
>  Разрешение использования нерегламентированных имен означает, что любой пользователь, прошедший проверку подлинности при входе в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , будет иметь доступ к поставщику. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] следует включить эту функцию для поставщиков, любой локальный доступ к которым не представляет опасности.  
  
## <a name="remarks"></a>Remarks  
 Попытка установки нерегламентированного соединения без включенной функции **Нерегламентированные распределенные запросы** приведет к ошибке. Сообщение 7415, уровень 16, состояние 1, строка 1  
  
 Нерегламентированный доступ к поставщику OLE DB «Microsoft.ACE.OLEDB.12.0» запрещен. К данному поставщику доступ необходимо производить через связанный сервер.  
  
## <a name="examples"></a>Примеры  
 Следующий пример включает распределенные нерегламентированные запросы и выполняет запрос к серверу `Seattle1` с использованием функции `OPENROWSET` .  
  
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
  
## <a name="see-also"></a>См. также:  
 [Параметры конфигурации сервера (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [Связанные серверы (компонент Database Engine)](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [OPENROWSET (Transact-SQL)](../../t-sql/functions/openrowset-transact-sql.md)   
 [OPENDATASOURCE (Transact-SQL)](../../t-sql/functions/opendatasource-transact-sql.md)   
 [sp_addlinkedserver (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)  
  
  

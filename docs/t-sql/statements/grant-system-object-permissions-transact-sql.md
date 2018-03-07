---
title: "Разрешения объекта GRANT системы (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 07/26/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- encryption [SQL Server], system objects
- system objects [SQL Server]
- GRANT statement, system objects
ms.assetid: 9d4e89f4-478f-419a-8b50-b096771e3880
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 68fc428edb12c5b62d5e6eadb6d92bc090e66fde
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="grant-system-object-permissions-transact-sql"></a>GRANT, предоставление разрешения на системный объект (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Предоставляет разрешения на доступ к таким системным объектам, как системные хранимые процедуры, расширенные хранимые процедуры, функции и представления.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
GRANT { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
## <a name="arguments"></a>Аргументы  
 [sys]. .  
 Квалификатор sys обязателен только при обращении к представлениям каталогов и к динамическим административным представлениям.  
  
 *system_object*  
 Задает объект, для которого предоставляется разрешение.  
  
 *Участник*  
 Участник, которому предоставляется разрешение.  
  
## <a name="remarks"></a>Замечания  
 Данная инструкция может быть использована для предоставления разрешений на доступ к определенным хранимым процедурам, расширенным хранимым процедурам, функциям с табличным значением, скалярным функциям, представлениям, представлениям каталогов и совместимостей, представлениям INFORMATION_SCHEMA, динамическим административным представлениям, а также системным таблицам, установленным [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждый из этих системных объектов существует в виде уникальной записи в базе данных ресурсов сервера (mssqlsystemresource). которая доступна только для чтения. Ссылка на объект представляется в виде записи в схеме sys для каждой базы данных. Разрешение на выполнение или выбор системного объекта может быть предоставлено, запрещено или отозвано.  
  
 Предоставление разрешения на выполнение или выбор объекта не подразумевает обязательного наличия других разрешений на использование данного объекта. В большинстве случаев для действий над объектами необходимо обладать дополнительными разрешениями. Например, пользователь, обладающий разрешением EXECUTE на процедуру sp_addlinkedserver, но при этом не являющийся членом предопределенной роли сервера sysadmin, не имеет права создавать связанные серверы.  
  
 Разрешение имен по умолчанию устраняет проблему неправомочных имен процедур в базе данных ресурсов. Поэтому квалификатор sys обязателен только при указании представлений каталогов и динамических административных представлений.  
  
 Разрешение на доступ к триггерам и столбцам системных объектов не предоставляется.  
  
 При обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешения на доступ к системным объектам сохраняются.  
  
 Системные объекты отображаются в представлении каталога [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) . Разрешения на системные объекты отображаются в [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) каталога представления в базе данных master.  
  
 В результате выполнения следующего запроса извлекаются данные о разрешениях на доступ к системным объектам:  
  
```  
SELECT * FROM master.sys.database_permissions AS dp   
    JOIN sys.system_objects AS so  
    ON dp.major_id = so.object_id  
    WHERE dp.class = 1 AND so.parent_object_id = 0 ;  
GO  
```  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-granting-select-permission-on-a-view"></a>A. Предоставление разрешения SELECT на представление  
 В следующем примере предоставляется [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] входа `Sylvester1` разрешения на выбор представления, отображающего [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] имена входа. Затем предоставляется дополнительное разрешение на просмотр метаданных имен входа [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], принадлежащих другим пользователям.  
  
```  
USE AdventureWorks2012;  
GRANT SELECT ON sys.sql_logins TO Sylvester1;  
GRANT VIEW SERVER STATE to Sylvester1;  
GO  
```  
  
### <a name="b-granting-execute-permission-on-an-extended-stored-procedure"></a>Б. Предоставление разрешения EXECUTE на расширенную хранимую процедуру  
 В следующем примере имени входа `EXECUTE` предоставляется разрешение `xp_readmail` на процедуру `Sylvester1`.  
  
```  
GRANT EXECUTE ON xp_readmail TO Sylvester1;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.system_objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [ОТОЗВАТЬ разрешения на системный объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)   
 [ЗАПРЕТ разрешений на системные объекты &#40; Transact-SQL &#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)  
  
  

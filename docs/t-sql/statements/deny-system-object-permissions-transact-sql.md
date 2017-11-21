---
title: "Запрет разрешения на системный объект (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
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
- DENY statement, system objects
- encryption [SQL Server], system objects
- system objects [SQL Server]
- cryptography [SQL Server], system objects
ms.assetid: 4e43f954-0982-470b-a239-08a13c61563a
caps.latest.revision: 21
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 563210a6798b6b3886ab2b62dc2204ff4d77b243
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="deny-system-object-permissions-transact-sql"></a>DENY, запрет разрешений на системные объекты (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  Запрещает разрешения для системных объектов, например хранимых процедур, расширенных хранимых процедур, функций и представлений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DENY { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
## <a name="arguments"></a>Аргументы  
 [ **sys.** ]  
 **Sys** квалификатор требуется только при обращении к представлениям каталогов и динамические административные представления.  
  
 *system_object*  
 Указывает объект, для которого запрещается разрешение.  
  
 *Участник*  
 Задает участника, у которого отменяется разрешение.  
  
## <a name="remarks"></a>Замечания  
 Эта инструкция может быть использована, чтобы запретить разрешения для определенных хранимых процедур, расширенных хранимых процедур, функций с табличным значением, скалярных функций, представлений, представлений каталога, представлений совместимости, представлений INFORMATION_SCHEMA, динамических административных представлений и системных таблиц, установленных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждый из этих системных объектов существует в виде уникальной записи в базе данных ресурсов (**mssqlsystemresource**). которая доступна только для чтения. Ссылка на объект представлена как запись в **sys** каждой базы данных.  
  
 Разрешение имен по умолчанию устраняет проблему неправомочных имен процедур в базе данных ресурсов. Таким образом **sys** квалификатор является только при указании представлений каталога и динамические административные представления.  
  
> [!CAUTION]  
>  Запрет разрешений в системных объектах вызовет ошибки в зависящих от них приложениях. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] используются представления каталогов, и нормальная работа может быть нарушена, если изменить разрешения по умолчанию для представлений каталогов.  
  
 Запрещение разрешений для триггеров и для столбцов системных объектов не поддерживается.  
  
 При обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешения на доступ к системным объектам сохраняются.  
  
 Системные объекты отображаются в представлении каталога [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) . Разрешения на доступ к системным объектам отображаются в представлении каталога [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) в базе данных **master** .  
  
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
 В следующем примере роли `EXECUTE` запрещается разрешение `xp_cmdshell` для расширенной процедуры `public`.  
  
```  
DENY EXECUTE ON sys.xp_cmdshell TO public;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Синтаксические обозначения Transact-SQL &#40; Transact-SQL &#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)   
 [sys.database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [ПРЕДОСТАВЬТЕ разрешения на системный объект &#40; Transact-SQL &#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [ОТОЗВАТЬ разрешения на системный объект &#40; Transact-SQL &#41;](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)  
  
  


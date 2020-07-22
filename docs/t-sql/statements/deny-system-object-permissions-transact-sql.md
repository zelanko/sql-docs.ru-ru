---
title: DENY, запрет разрешений на системные объекты (Transact-SQL) | Документы Майкрософт
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- DENY statement, system objects
- encryption [SQL Server], system objects
- system objects [SQL Server]
- cryptography [SQL Server], system objects
ms.assetid: 4e43f954-0982-470b-a239-08a13c61563a
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: e4e866d6cc2c117599f276b51569321cc2ba6107
ms.sourcegitcommit: edba1c570d4d8832502135bef093aac07e156c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/20/2020
ms.locfileid: "86484165"
---
# <a name="deny-system-object-permissions-transact-sql"></a>DENY, запрет разрешений на системные объекты (Transact-SQL)
[!INCLUDE [SQL Server SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Запрещает разрешения для системных объектов, например хранимых процедур, расширенных хранимых процедур, функций и представлений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```syntaxsql
  
DENY { SELECT | EXECUTE } ON [ sys.]system_object TO principal   
```  
  
[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## <a name="arguments"></a>Аргументы
 [ **sys.** ]  
 Квалификатор **sys** требуется только тогда, когда имеется ссылка на представления каталога и динамические административные представления.  
  
 *system_object*  
 Указывает объект, для которого запрещается разрешение.  
  
 *principal*  
 Задает участника, у которого отменяется разрешение.  
  
## <a name="remarks"></a>Remarks  
 Эта инструкция может быть использована, чтобы запретить разрешения для определенных хранимых процедур, расширенных хранимых процедур, функций с табличным значением, скалярных функций, представлений, представлений каталога, представлений совместимости, представлений INFORMATION_SCHEMA, динамических административных представлений и системных таблиц, установленных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждый из этих системных объектов существует в виде уникальной записи в базе данных ресурсов (**mssqlsystemresource**). Она доступна только для чтения. Ссылка на объект представлена в виде записи в схеме **sys** каждой базы данных.  
  
 Разрешение имен по умолчанию устраняет проблему неправомочных имен процедур в базе данных ресурсов. Следовательно, квалификатор **sys** требуется только при указании представлений каталога и динамических административных представлений.  
  
> [!CAUTION]  
>  Запрет разрешений в системных объектах вызовет ошибки в зависящих от них приложениях. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] используются представления каталогов, и нормальная работа может быть нарушена, если изменить разрешения по умолчанию для представлений каталогов.  
  
 Запрещение разрешений для триггеров и для столбцов системных объектов не поддерживается.  
  
 При обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешения на доступ к системным объектам сохраняются.  
  
 Системные объекты отображаются в представлении каталога [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md). Разрешения на доступ к системным объектам отображаются в представлении каталога [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md) в базе данных **master**.  
  
 В результате выполнения следующего запроса извлекаются данные о разрешениях на доступ к системным объектам:  
  
```  
SELECT * FROM master.sys.database_permissions AS dp   
    JOIN sys.system_objects AS so  
    ON dp.major_id = so.object_id  
    WHERE dp.class = 1 AND so.parent_object_id = 0 ;  
GO  
```  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере запрещается разрешение `EXECUTE` на `xp_cmdshell` для `public`.  
  
```  
DENY EXECUTE ON sys.xp_cmdshell TO public;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Синтаксические обозначения в Transact-SQL (Transact-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)   
 [sys.database_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [GRANT, предоставление разрешения на системный объект (Transact-SQL)](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [REVOKE, отмена разрешений на системный объект (Transact-SQL)](../../t-sql/statements/revoke-system-object-permissions-transact-sql.md)  
  
  

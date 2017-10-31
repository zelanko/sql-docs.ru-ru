---
title: "ОТОЗВАТЬ разрешения на системный объект (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, system objects
- permissions [SQL Server], system objects
ms.assetid: 84983238-dd7d-45bd-99bb-52c9d8e96a87
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17b371e839d27c065628def8a7be56e6bef650a0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-system-object-permissions-transact-sql"></a>REVOKE, отмена разрешения на системные объекты (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отменяет для участника разрешения на системные объекты (например, хранимые процедуры, расширенные хранимые процедуры, функции и представления).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
REVOKE { SELECT | EXECUTE } ON [sys.]system_object FROM principal   
```  
  
## <a name="arguments"></a>Аргументы  
 [**sys.** ] .  
 **Sys** квалификатор требуется только при обращении к представлениям каталогов и динамические административные представления.  
  
 *system_object*  
 Задает объект, для которого отменяется разрешение.  
  
 *Участник*  
 Задает участника, у которого отменяется разрешение.  
  
## <a name="remarks"></a>Замечания  
 Эта инструкция предназначена для отмены разрешений на хранимые процедуры, расширенные хранимые процедуры, функции с табличным значением и скалярные функции, представления, представления каталога, представления совместимости, представления INFORMATION_SCHEMA, динамические административные представления и системные таблицы, которые устанавливаются в составе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Каждый из этих системных объектов существует в виде уникальной записи в базе данных ресурсов (**mssqlsystemresource**). которая доступна только для чтения. Ссылка на объект представлена как запись в **sys** каждой базы данных.  
  
 Разрешение имен по умолчанию устраняет проблему неправомочных имен процедур в базе данных ресурсов. Таким образом **sys.** Квалификатор требуется только при указании представлений каталога и динамические административные представления.  
  
> [!CAUTION]  
>  Вызов разрешений в системных объектах вызовет ошибки в зависящих от них приложениях. В [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] используются представления каталогов, и нормальная работа может быть нарушена, если изменить разрешения по умолчанию для представлений каталогов.  
  
 Отмена разрешений на триггеры и столбцы системных объектов не поддерживается.  
  
 При обновлении [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] разрешения на доступ к системным объектам сохраняются.  
  
 Системные объекты отображаются в представлении каталога [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) .  
  
## <a name="permissions"></a>Permissions  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="examples"></a>Примеры  
 В следующем примере производится отмена разрешения `EXECUTE` на процедуру `sp_addlinkedserver` у роли `public`.  
  
```  
REVOKE EXECUTE ON sys.sp_addlinkedserver FROM public;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [sys.system_objects &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.database_permissions &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [ПРЕДОСТАВЬТЕ разрешения на системный объект &#40; Transact-SQL &#41;](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [ЗАПРЕТ разрешений на системные объекты &#40; Transact-SQL &#41;](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)  
  
  


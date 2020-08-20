---
description: sys.fn_translate_permissions (Transact-SQL)
title: sys. fn_translate_permissions (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.fn_translate_permissions
- sys.fn_translate_permissions_TSQL
- fn_translate_permissions
- fn_translate_permissions_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- permissions bitmask [SQL Server]
- sys.fn_translate_permissions function
- fn_translate_permissions function
ms.assetid: ac97121f-2bd0-4f71-8e45-42c8584edbc5
author: rothja
ms.author: jroth
ms.openlocfilehash: 1069d5b76d6ee404ddd2e671eb6a7b63396424ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88481769"
---
# <a name="sysfn_translate_permissions-transact-sql"></a>sys.fn_translate_permissions (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Преобразует битовую маску разрешений, возвращаемую трассировкой SQL, в таблицу имен разрешений.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sys.fn_translate_permissions ( level , perms )  
```  
  
## <a name="arguments"></a>Аргументы  
 *уровень*  
 Вид защищаемого объекта, к которому применяется разрешение. *Level* имеет тип **nvarchar (60)**.  
  
 *perms*  
 Битовая маска, возвращаемая в столбце разрешений. *разрешение* имеет тип **varbinary (16)**.  
  
## <a name="returns"></a>Возвращаемое значение  
 **table**  
  
## <a name="remarks"></a>Комментарии  
 Значение, возвращаемое в столбце **Permissions** трассировки SQL, является целочисленным представлением битовой маски, используемой [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для вычисления действующих разрешений. Каждый из 25 вида защищаемых объектов имеет собственный набор разрешений с соответствующими числовыми значениями. **sys. fn_translate_permissions** преобразует эту битовую маску в таблицу имен разрешений.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо быть членом роли **public**.  
  
## <a name="example"></a>Пример  
 Следующий запрос использует `sys.fn_builtin_permissions` для отображения разрешений, которые применяются к сертификатам, а затем использует `sys.fn_translate_permissions` для получения результатов битовой маски разрешений.  
  
```  
SELECT * FROM sys.fn_builtin_permissions('CERTIFICATE');  
SELECT '0001' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0001);  
SELECT '0010' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0010);  
SELECT '0011' AS Input, * FROM sys.fn_translate_permissions('CERTIFICATE', 0011);  
```  
  
## <a name="see-also"></a>См. также  
 [Разрешения (ядро СУБД)](../../relational-databases/security/permissions-database-engine.md)   
 [sys.server_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-permissions-transact-sql.md)   
 [sys.database_permissions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)  
  
  

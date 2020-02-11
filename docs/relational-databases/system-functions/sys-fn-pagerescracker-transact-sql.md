---
title: sys. fn_PageResCracker (Transact-SQL) | Документация Майкрософт
description: Документация по системной функции sys. fn_PageResCracker.
ms.custom: ''
ms.date: 09/18/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_PageResCracker
- sys.fn_PageResCracker_TSQL
- fn_PageResCracker_TSQL
- sys.fn_PageResCracker
- sys.dm_db_page_info
dev_langs:
- TSQL
helpviewer_keywords:
- fn_PageResCracker function
- page_resource
- sys.fn_PageResCracker function
- sys.dm_db_page_info
- page info
author: bluefooted
ms.author: pamela
manager: amitban
ms.openlocfilehash: 6d8203979a0afdca1ae78b9bd51723c906c40ea2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "68267073"
---
# <a name="sysfn_pagerescracker-transact-sql"></a>sys. fn_PageResCracker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Возвращает `db_id`, `file_id`и `page_id` для заданного `page_resource` значения. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
```  
sys.fn_PageResCracker ( page_resource )  
```  
  
## <a name="arguments"></a>Аргументы  
*page_resource*    
Является 8-байтовым шестнадцатеричным форматом ресурса страницы базы данных.
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
  
|Имя столбца|Тип данных|Description|  
|-----------------|---------------|-----------------|  
|db_id|**int**|Идентификатор базы данных|  
|file_id|**int**|Идентификатор файла|  
|page_id|**int**|Идентификатор страницы|  
  
## <a name="remarks"></a>Remarks  
`sys.fn_PageResCracker`используется для преобразования 8-байтового шестнадцатеричного представления страницы базы данных в набор строк, содержащий идентификатор базы данных, идентификатор файла и идентификатор страницы.   

Допустимый ресурс страницы можно получить из `page_resource` столбца в динамическом административном представлении [sys. dm_exec_requests &#40;transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) или в системном представлении [sys. sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) . Если используется недопустимый ресурс страницы, возвращается значение NULL.  
Основное использование функции `sys.fn_PageResCracker` заключается в упрощении соединений между этими представлениями и функцией динамического управления [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) для получения сведений о странице, например объекта, которому она принадлежит.
  
## <a name="permissions"></a>Разрешения  
Пользователю требуется `VIEW SERVER STATE` разрешение на сервере.  
  
## <a name="examples"></a>Примеры  
Функцию можно использовать в сочетании с [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) для устранения неполадок, связанных с страницами, и блокировки в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sys.fn_PageResCracker`  Следующий сценарий является примером того, как можно использовать эти функции для сбора сведений о странице базы данных для всех активных запросов, ожидающих некоторого типа ресурса страницы. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>См. также:  
 [sys. dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [sys. sysprocesses &#40;&#41;Transact-SQL](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys. dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  

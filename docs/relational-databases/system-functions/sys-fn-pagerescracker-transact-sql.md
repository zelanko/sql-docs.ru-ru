---
title: sys.fn_PageResCracker (Transact-SQL) | Документация Майкрософт
description: Документация по sys.fn_PageResCracker системной функции.
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
ms.openlocfilehash: 2fc7136b60dba47813b9942316ee6fdfbc64f307
ms.sourcegitcommit: 323d2ea9cb812c688cfb7918ab651cce3246c296
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58899710"
---
# <a name="sysfnpagerescracker-transact-sql"></a>sys.fn_PageResCracker (Transact-SQL)
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Возвращает `db_id`, `file_id`, и `page_id` для заданного `page_resource` значение. 
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
```  
sys.fn_PageResCracker ( page_resource )  
```  
  
## <a name="arguments"></a>Аргументы  
*page_resource*    
— Это 8-байтное шестнадцатеричное формат ресурса страницы базы данных.
  
## <a name="tables-returned"></a>Возвращаемые таблицы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|db_id|**int**|Идентификатор базы данных|  
|file_id|**int**|Идентификатор файла|  
|page_id|**int**|Идентификатор страницы|  
  
## <a name="remarks"></a>Примечания  
`sys.fn_PageResCracker` используется для преобразования 8-байтное шестнадцатеричное представление страницы базы данных в набор строк, содержащий идентификатор базы данных, файл, идентификатор и идентификатор страницы.   

Вы может получить доступ к ресурсу действительных страниц из `page_resource` столбец [sys.dm_exec_requests &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md) динамического административного представления или [sys.sysprocesses &#40;Transact-SQL&#41; ](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md) системное представление. Если ресурс Недопустимая страница используется, то возвращается значение NULL.  
Главным образом используется `sys.fn_PageResCracker` облегчает соединения между этими представлениями и [sys.dm_db_page_info &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) функции динамического управления, чтобы получить сведения о странице, такие как Объект, к которой он принадлежит.
  
## <a name="permissions"></a>Разрешения  
Нужные пользователю `VIEW SERVER STATE` разрешение на сервере.  
  
## <a name="examples"></a>Примеры  
`sys.fn_PageResCracker` Функция может использоваться в сочетании с [sys.dm_db_page_info &#40;Transact-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md) для устранения неполадок страница и связанные с ожиданий блокировок в [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  Следующий сценарий — пример того, как эти функции можно использовать для сбора сведений о всех активных запросов, ожидающих на некоторый тип ресурса страницы страницы базы данных. 
  
```sql  
SELECT page_info.* 
FROM sys.dm_exec_requests AS d  
CROSS APPLY sys.fn_PageResCracker (d.page_resource) AS r  
CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id, 1) AS page_info
```  
  
## <a name="see-also"></a>См. также  
 [sys.dm_db_page_info &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql.md)  
 [sys.sysprocesses &#40;Transact-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysprocesses-transact-sql.md)   
 [sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  
  
  

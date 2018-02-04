---
title: "sys.sp_xtp_unbind_db_resource_pool (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_xtp_unbind_db_resource_pool_TSQL
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool_TSQL
- sys.sp_xtp_unbind_db_resource_pool
dev_langs:
- TSQL
helpviewer_keywords:
- sp_xtp_unbind_db_resource_pool
- sys.sp_xtp_unbind_db_resource_pool
ms.assetid: 695a796d-087e-4bc8-99d0-ddc342604c75
caps.latest.revision: 
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9c28c3fd5e535bfff09316c1f813760159f05d38
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="sysspxtpunbinddbresourcepool-transact-sql"></a>sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Эта системная процедура удаляет существующую привязку между базой данных и пулом ресурсов для отслеживания использования памяти [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  Если в настоящий момент ни один пул не привязан к указанной базе данных, возвращается значение «успех». Если база данных не имеет привязки, ранее выделенная память для оптимизированных для памяти объектов остается выделенной для предыдущего пула ресурсов. Необходимо перезапустить базу данных, чтобы освободить выделенную память. После отвязки базы данных от пула ресурсов привязка возвращается к пулу ресурсов по умолчанию.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'database_name'  
```  
  
## <a name="arguments"></a>Аргументы  
 database_name  
 Имя существующей базы данных с подключенными [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  
  
#### <a name="parameters"></a>Параметры  
  
## <a name="messages"></a>Сообщения  
 Если база данных была привязана к именованному пулу ресурсов, процедура возвращает значение «успешно». Однако необходимо перезапустить базу данных для отмены привязки, чтобы изменения вступили в силу.  
 Если для существующей базы данных не указана привязка, `sp_xtp_unbind_db_resource_pool` возвращает значение «успешно», однако выводится информационное сообщение:  
  
```  
Msg 41374, Level 16, State 1, Procedure sp_xtp_unbind_db_resource_pool_internal, Line 140.  
Database 'Hekaton_DB' does not have a binding to a resource pool.  
  
```  
  
## <a name="example"></a>Пример  
 Следующий код позволяет отвязать базу данных Hekaton_DB от пула ресурсов [!INCLUDE[hek_2](../../includes/hek-2-md.md)], к которому он привязан.  Если Hekaton_DB в настоящее время не привязана к пулу ресурсов [!INCLUDE[hek_2](../../includes/hek-2-md.md)], выводится сообщение. База данных должна быть перезапущена, чтобы отмена привязки вступила в силу.  
  
```sql  
sys.sp_xtp_unbind_db_resource_pool 'Hekaton_DB'  
```  
  
## <a name="requirements"></a>Требования  
  
-   База данных, указанная в `database_name`, должна иметь привязку к пулу ресурсов [!INCLUDE[hek_2](../../includes/hek-2-md.md)].  
  
-   Необходимо разрешение CONTROL SERVER.  
  
## <a name="see-also"></a>См. также  
 [Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool &#40; Transact-SQL &#41;](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)  
  
  

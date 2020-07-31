---
title: sys. sp_xtp_unbind_db_resource_pool (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: de629f6ae966f8ea64dffa01676811650ac38b43
ms.sourcegitcommit: 039fb38c583019b3fd06894160568387a19ba04e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/30/2020
ms.locfileid: "87442635"
---
# <a name="syssp_xtp_unbind_db_resource_pool-transact-sql"></a>sys.sp_xtp_unbind_db_resource_pool (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

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
  
## <a name="see-also"></a>См. также:  
 [Привязка базы данных с таблицами, оптимизированными для памяти, к пулу ресурсов](../../relational-databases/in-memory-oltp/bind-a-database-with-memory-optimized-tables-to-a-resource-pool.md)   
 [sys.sp_xtp_bind_db_resource_pool (Transact-SQL)](../../relational-databases/system-stored-procedures/sys-sp-xtp-bind-db-resource-pool-transact-sql.md)  
  
  

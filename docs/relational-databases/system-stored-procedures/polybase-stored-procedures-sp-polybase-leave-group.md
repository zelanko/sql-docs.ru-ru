---
title: sp_polybase_leave_group (Transact-SQL) | Документация Майкрософт
description: Sp_polybase_leave_group команда Transact-SQL удаляет экземпляр SQL Server из группы Polybase для вычисления масштабного масштабирования.
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: polybase
ms.topic: conceptual
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords:
- sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3d909da06b0f8cf4520d92a9ba8cb8652a6b2a5a
ms.sourcegitcommit: 968969b62bc158b9843aba5034c9d913519bc4a7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/06/2020
ms.locfileid: "91753898"
---
# <a name="sp_polybase_leave_group-transact-sql"></a>sp_polybase_leave_group (Transact-SQL)
[!INCLUDE [sqlserver2016](../../includes/applies-to-version/sqlserver2016.md)]

  Удаляет SQL Server экземпляр из группы Polybase для масштабируемых вычислений. 
 
 На экземпляре SQL Server должна быть установлена функция  [руководств по polybase](../../relational-databases/polybase/polybase-guide.md) .  Polybase обеспечивает интеграцию источников данных, отличных от SQL Server, таких как Hadoop и хранилище BLOB-объектов Azure. См. также [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL SERVER.  
  
## <a name="remarks"></a>Комментарии  
 Из группы можно удалить только один из вычислений.  
  
 После выполнения хранимой процедуры перезапустите ядро Polybase и службу Перемещение данных PolyBase на компьютере. Чтобы проверить, выполняется ли следующее динамическое административное представление на головном узле: **sys.dm_exec_compute_nodes**.  
  
## <a name="example"></a>Пример  
 В этом примере удаляется текущий компьютер из группы Polybase.  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе с PolyBase](../polybase/polybase-guide.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  

---
title: sp_polybase_leave_group (Transact-SQL) | Документация Майкрософт
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 0071746f2d65dd0c9c699beeacf404bf3dd7bb65
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941927"
---
# <a name="sppolybaseleavegroup-transact-sql"></a>sp_polybase_leave_group (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Удаляет экземпляр SQL Server из группы PolyBase для масштабируемых вычислений. 
 
 Экземпляр SQL Server должен иметь [руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md) установлен компонент.  PolyBase позволяет интегрировать источников данных SQL Server, таких как Hadoop и Azure хранилище BLOB-объектов. См. также [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Требуется разрешение CONTROL SERVER.  
  
## <a name="remarks"></a>Примечания  
 Вычислительный узел можно только удалить из группы.  
  
 После выполнения хранимой процедуры, перезапустите ядро PolyBase и служба перемещения данных PolyBase на компьютере. Для проверки выполнения следующему динамическому административному Представлению на головном узле: **sys.dm_exec_compute_nodes**.  
  
## <a name="example"></a>Пример  
 В примере удаляется текущего компьютера из группы PolyBase.  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

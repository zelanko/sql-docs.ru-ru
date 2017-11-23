---
title: "sp_polybase_leave_group (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine-polybase
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sp_polybase_leave_group
- sp_polybase_leave_group_TSQL
helpviewer_keywords: sp_polybase_leave_group
ms.assetid: ef87a8f1-5407-47b5-b8bf-bd7d08c0f0fe
caps.latest.revision: "11"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f86b26be75bfc5311714c969c9d965152a8acf5f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="polybase-stored-procedures---sppolybaseleavegroup"></a>Хранимые процедуры PolyBase - sp_polybase_leave_group
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Удаляет экземпляр SQL Server из группу PolyBase для вычислений с горизонтальным масштабированием. 
 
 Экземпляр SQL Server должен иметь [руководство по PolyBase](../../relational-databases/polybase/polybase-guide.md) установлен компонент.  PolyBase позволяет интегрировать источников данных SQL Server, например Hadoop и Azure хранилища больших двоичных объектов. См. также [sp_polybase_join_group](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-join-group.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_polybase_leave_group;  
  
```  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Permissions  
 Требуется разрешение CONTROL SERVER.  
  
## <a name="remarks"></a>Замечания  
 Вычислительный узел можно только удалить из группы.  
  
 После выполнения хранимой процедуры, перезапустите ядро PolyBase и служба перемещения данных PolyBase на компьютере. Для проверки выполнения следующих динамических административных Представлений на головном узле: **sys.dm_exec_compute_nodes**.  
  
## <a name="example"></a>Пример  
 В примере текущий компьютер удаляется из группы PolyBase.  
  
```sql  
EXEC sp_polybase_leave_group ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

---
title: "sp_polybase_join_group | Документы Microsoft"
ms.custom: 
ms.date: 05/24/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sp_polybase_join_group
helpviewer_keywords:
- PolyBase
ms.assetid: 48066431-fed2-4a8a-85af-ac704689e183
caps.latest.revision: 
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7f6e4a77e5ce1341269bf9220c5d2a5305b4c314
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/03/2018
---
# <a name="polybase-stored-procedures---sppolybasejoingroup"></a>Хранимые процедуры PolyBase - sp_polybase_join_group
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Добавляет экземпляр SQL Server вычислительным узлом в группу PolyBase для вычислений с горизонтальным масштабированием.  
  
 Экземпляр SQL Server должен иметь [PolyBase](../../relational-databases/polybase/polybase-guide.md) установлен компонент.  PolyBase позволяет интегрировать источников данных SQL Server, например Hadoop и Azure хранилища больших двоичных объектов. См. также [sp_polybase_leave_group &#40; Transact-SQL &#41; ](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_polybase_join_group (@head_node_address = N'head_node_address',  
    @dms_control_channel_port = dms_control_channel_port,  
    @head_node_sql_server_instance_name = head_node_sql_server_instance_name)  
[ ; ]          
```  
  
## <a name="arguments"></a>Аргументы  
 *@head_node_address* = N'*head_node_address*'  
 Имя компьютера, на котором размещается SQL Server головной узел масштабируемой группы PolyBase. *@head_node_address*имеет тип nvarchar(255).  
  
 *@dms_control_channel_port* = dms_control_channel_port  
 Порт, где запущен канал управления для головного узла службы перемещения данных PolyBase. *@dms_control_channel_port*Это число без знака __int16. Значение по умолчанию — **16450**.  
  
 *@head_node_sql_server_instance_name* = head_node_sql_server_instance_name  
 Имя экземпляра SQL Server головного узла в масштабируемой группе PolyBase. *@head_node_sql_server_instance_name*— nvarchar(16) в формате.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="remarks"></a>Remarks  
 После выполнения хранимой процедуры, завершите работу ядра PolyBase и перезапустите службу перемещения данных PolyBase на компьютере. Для проверки выполнения следующих динамических административных Представлений на головном узле: **sys.dm_exec_compute_nodes**.  
  
## <a name="example"></a>Пример  
 В примере объединяются текущего компьютера как вычислительного узла группы PolyBase.  Имя головного узла — **HST01** и имя экземпляра SQL Server на головном узле **MSSQLSERVER**.  
  
```  
EXEC sp_polybase_join_group N'HST01', 16450, N'MSSQLSERVER'   
```  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

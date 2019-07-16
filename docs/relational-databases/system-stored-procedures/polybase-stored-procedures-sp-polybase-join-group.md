---
title: sp_polybase_join_group | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sp_polybase_join_group
helpviewer_keywords:
- PolyBase
ms.assetid: 48066431-fed2-4a8a-85af-ac704689e183
author: rothja
ms.author: jroth
ms.openlocfilehash: 0b7be2bb99a92794ed8c1b5971edca47522c2552
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67941939"
---
# <a name="sppolybasejoingroup-transact-sql"></a>sp_polybase_join_group (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Добавляет экземпляр SQL Server в качестве вычислительного узла в группу PolyBase для масштабируемых вычислений.  
  
 Экземпляр SQL Server должен иметь [PolyBase](../../relational-databases/polybase/polybase-guide.md) установлен компонент.  PolyBase позволяет интегрировать источников данных SQL Server, таких как Hadoop и Azure хранилище BLOB-объектов. См. также [sp_polybase_leave_group &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/polybase-stored-procedures-sp-polybase-leave-group.md).  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_polybase_join_group (@head_node_address = N'head_node_address',  
    @dms_control_channel_port = dms_control_channel_port,  
    @head_node_sql_server_instance_name = head_node_sql_server_instance_name)  
[ ; ]          
```  
  
## <a name="arguments"></a>Аргументы  
 *@head_node_address* = N "*head_node_address*"  
 Имя компьютера, на котором размещается SQL Server головной узел масштабируемой группы PolyBase. *@head_node_address* имеет тип nvarchar(255).  
  
 *@dms_control_channel_port* = dms_control_channel_port  
 Порт, где выполняется канал управления для головного узла службы перемещения данных PolyBase. *@dms_control_channel_port* является __int16 без знака. По умолчанию используется **16450**.  
  
 *@head_node_sql_server_instance_name* = head_node_sql_server_instance_name  
 Имя экземпляра SQL Server головного узла в масштабируемой группе PolyBase. *@head_node_sql_server_instance_name* — nvarchar(16) в формате.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 0 (успешное завершение) или 1 (неуспешное завершение)  
  
## <a name="permissions"></a>Разрешения  
 Необходимо разрешение CONTROL SERVER.  
  
## <a name="remarks"></a>Примечания  
 После выполнения хранимой процедуры, завершите работу ядра PolyBase и перезапустите службу перемещения данных PolyBase на компьютере. Для проверки выполнения следующему динамическому административному Представлению на головном узле: **sys.dm_exec_compute_nodes**.  
  
## <a name="example"></a>Пример  
 В примере объединяются текущего компьютера в качестве вычислительного узла в группу PolyBase.  Имя головного узла — **HST01** и имя экземпляра SQL Server на головном узле **MSSQLSERVER**.  
  
```  
EXEC sp_polybase_join_group N'HST01', 16450, N'MSSQLSERVER'   
```  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе с PolyBase](../../relational-databases/polybase/get-started-with-polybase.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

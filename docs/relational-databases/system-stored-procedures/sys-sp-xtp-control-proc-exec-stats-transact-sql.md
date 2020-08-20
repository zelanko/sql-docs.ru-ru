---
description: sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
title: sys. sp_xtp_control_proc_exec_stats (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sp_xtp_control_proc_exec_stats
- sys.sp_xtp_control_proc_exec_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_xtp_control_proc_exec_stats
ms.assetid: f5119808-76a1-4522-8529-9e02ee39adcb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: e189cd4e7a5ec9f488cce78ee6cc159c8700a463
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88473411"
---
# <a name="syssp_xtp_control_proc_exec_stats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[sqlserver](../../includes/applies-to-version/sqlserver.md)]

  Включает сбор статистики для скомпилированных в собственном коде хранимых процедур экземпляра.  
  
 Сведения о включении сбора статистики на уровне запроса для скомпилированных в собственном режиме хранимых процедур см. в разделе [sys. sp_xtp_control_query_exec_stats &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>Аргументы  
 @new_collection_value = *значение*  
 Определяет, включен (1) или выключен (0) сбор статистики на уровне процедуры.  
  
 @new_collection_value При [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запуске или базы данных устанавливается в ноль.  
  
 @old_collection_value = *значение*  
 Возвращает текущее состояние.  
  
## <a name="return-code"></a>Код возврата  
 0 — успешное завершение. Ненулевое значение — ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли sysadmin.  
  
## <a name="code-samples"></a>Примеры кода  
 Установка @new_collection_value и запрос значения @new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

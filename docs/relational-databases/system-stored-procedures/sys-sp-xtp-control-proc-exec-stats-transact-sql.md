---
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
author: stevestein
ms.author: sstein
ms.openlocfilehash: 14c45f5ba725ef8d9cc498b1049c5a71c80a6d7a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "67909226"
---
# <a name="syssp_xtp_control_proc_exec_stats-transact-sql"></a>sys.sp_xtp_control_proc_exec_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  Включает сбор статистики для скомпилированных в собственном коде хранимых процедур экземпляра.  
  
 Сведения о включении сбора статистики на уровне запроса для скомпилированных в собственном режиме хранимых процедур см. в разделе [sys. sp_xtp_control_query_exec_stats &#40;&#41;Transact-SQL ](../../relational-databases/system-stored-procedures/sys-sp-xtp-control-query-exec-stats-transact-sql.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
sp_xtp_control_proc_exec_stats [ [ @new_collection_value = ] collection_value ], [ @old_collection_value]  
```  
  
## <a name="arguments"></a>Аргументы  
 @new_collection_value= *значение*  
 Определяет, включен (1) или выключен (0) сбор статистики на уровне процедуры.  
  
 @new_collection_valueПри [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] запуске или базы данных устанавливается в ноль.  
  
 @old_collection_value= *значение*  
 Возвращает текущее состояние.  
  
## <a name="return-code"></a>Код возврата  
 0 — успешное завершение. Ненулевое значение — ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Необходимо членство в предопределенной роли sysadmin.  
  
## <a name="code-samples"></a>Примеры кода  
 Установка @new_collection_value и запрос значения@new_collection_value:  
  
```  
exec [sys].[sp_xtp_control_proc_exec_stats] @new_collection_value = 1  
declare @c bit  
exec sp_xtp_control_proc_exec_stats @old_collection_value=@c output  
select @c as 'collection status'  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

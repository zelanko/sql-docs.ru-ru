---
title: sp_syscollector_run_collection_set (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_run_collection_set_TSQL
- sp_syscollector_run_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_run_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 7bbaee48-dfc7-45c0-b11f-c636b6a7e720
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e2ad81b1d92bb45d9ab15ca11897804cc0d333a9
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58531406"
---
# <a name="spsyscollectorruncollectionset-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Запускает набор сбора в случае, если сборщик данных уже включен, а набор сбора настроен на сбор без кэширования.  
  
> [!NOTE]  
>  Эта процедура завершится со сбоем, если она будет запущена для набора сбора, настроенного на сбор с кэшированием.  
  
 Процедура sp_syscollector_run_collection_set позволяет пользователю создавать моментальные снимки данных по запросу.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_run_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @collection_set_id = ] collection_set_id` — Это уникальный локальный идентификатор набора элементов сбора. *collection_set_id* — **int** и должен иметь значение, если *имя* имеет значение NULL.  
  
`[ @name = ] 'name'` — Имя набора элементов сбора. *имя* — **sysname** и должен иметь значение, если *collection_set_id* имеет значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Либо *collection_set_id* или *имя* должен иметь значение, не может быть NULL.  
  
 Эта процедура будет начать сбор и отправка заданий для указанной коллекции набора, а также немедленно запускает задание агента сбора, если в наборе сбора есть его **@collection_mode** значение без кэширования (1). Дополнительные сведения см. [sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 Процедура sp_sycollector_run_collection_set также может быть использована для запуска набора сбора, не имеющего расписания.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **dc_operator** (с разрешением EXECUTE) предопределенной роли базы данных для выполнения этой процедуры.  
  
## <a name="example"></a>Пример  
 Запуск набора сбора с помощью его идентификатора.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_run_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  

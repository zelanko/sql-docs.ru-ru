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
ms.openlocfilehash: 3807a53921572bbe20b4c459bff34958cbb42001
ms.sourcegitcommit: 43c3d8939f6f7b0ddc493d8e7a643eb7db634535
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2019
ms.locfileid: "72304992"
---
# <a name="sp_syscollector_run_collection_set-transact-sql"></a>sp_syscollector_run_collection_set (Transact-SQL)
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
`[ @collection_set_id = ] collection_set_id` является уникальным локальным идентификатором набора сбора. *collection_set_id* имеет **тип int** и должен иметь значение, если *Name* имеет значение null.  
  
`[ @name = ] 'name'` — это имя набора элементов сбора. Аргумент *Name* имеет тип **sysname** и должен иметь значение, если *collection_set_id* имеет значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Либо *collection_set_id* , либо *Name* должны иметь значение null.  
  
 Эта процедура запускает сбор и передачу заданий для указанного набора сбора и немедленно запускает задание агента сбора, если для набора сбора **\@collection_mode** установлен некэшированный (1). Дополнительные сведения см. в [разделе &#40;SP_SYSCOLLECTOR_CREATE_COLLECTION_SET Transact-&#41;SQL](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
 Процедура sp_sycollector_run_collection_set также может быть использована для запуска набора сбора, не имеющего расписания.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных **dc_operator** (с разрешением EXECUTE).  
  
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
  
  

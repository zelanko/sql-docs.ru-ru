---
title: "sp_syscollector_upload_collection_set (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_upload_collection_set
- sp_syscollector_upload_collection_set_TSQL
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_upload_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc
caps.latest.revision: "19"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 0a175a632d68acd6ca9ae1842e8f1497fd03e42a
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectoruploadcollectionset-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Начинает передачу данных набора элементов сбора в том случае, если набор элементов сбора включен.  
  
> [!IMPORTANT]  
>  Эта хранимая процедура может использоваться только для наборов элементов сбора, настроенных для сбора и передачи данных в режиме с кэшированием.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_upload_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@collection_set_id =** ] *collection_set_id, чтобы выделить*  
 Уникальный локальный идентификатор набора элементов сбора. *collection_set_id, чтобы выделить* — **int** и должен иметь значение, если *имя* имеет значение NULL.  
  
 [  **@name =** ] **"***имя***"**  
 Имя набора элементов сбора. *имя* — **sysname** и должен иметь значение, если *collection_set_id, чтобы выделить* имеет значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Либо *collection_set_id, чтобы выделить* или *имя* должен иметь значение, и не может иметь значение NULL.  
  
 Данная процедура может использоваться для начала передачи работающего набора сбора по требованию. Она может использоваться только для наборов сбора, настроенных для сбора и передачи данных в режиме с кэшированием. Это позволяет пользователю получить данные для анализа, не ожидая запланированной передачи.  
  
## <a name="permissions"></a>Permissions  
 Требуется членство в **dc_operator** (с разрешением EXECUTE) предопределенной роли базы данных для выполнения этой процедуры.  
  
## <a name="example"></a>Пример  
 Выполняет по требованию передачу набора сбора `Simple Collection Set`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_upload_collection_set @name = 'Simple Collection Set' ;  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  

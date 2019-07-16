---
title: sp_syscollector_upload_collection_set (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_upload_collection_set
- sp_syscollector_upload_collection_set_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_upload_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: eed9232c-2b0a-4b6a-8ba0-76b7c99f48dc
author: stevestein
ms.author: sstein
ms.openlocfilehash: eb5b4b9dce229a028be45565203bce90883e21f3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68010528"
---
# <a name="spsyscollectoruploadcollectionset-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Начинает передачу данных набора элементов сбора в том случае, если набор элементов сбора включен.  
  
> [!IMPORTANT]  
>  Эта хранимая процедура может использоваться только для наборов элементов сбора, настроенных для сбора и передачи данных в режиме с кэшированием.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_upload_collection_set [[ @collection_set_id = ] collection_set_id ]  
          , [[ @name = ] 'name' ]   
```  
  
## <a name="arguments"></a>Аргументы  
`[ @collection_set_id = ] collection_set_id` — Это уникальный локальный идентификатор набора элементов сбора. *collection_set_id* — **int** и должен иметь значение, если *имя* имеет значение NULL.  
  
`[ @name = ] 'name'` — Имя набора элементов сбора. *имя* — **sysname** и должен иметь значение, если *collection_set_id* имеет значение NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 Либо *collection_set_id* или *имя* должен иметь значение; оба не может иметь значение NULL.  
  
 Данная процедура может использоваться для начала передачи работающего набора сбора по требованию. Она может использоваться только для наборов сбора, настроенных для сбора и передачи данных в режиме с кэшированием. Это позволяет пользователю получить данные для анализа, не ожидая запланированной передачи.  
  
## <a name="permissions"></a>Разрешения  
 Требуется членство в **dc_operator** (с разрешением EXECUTE) предопределенной роли базы данных для выполнения этой процедуры.  
  
## <a name="example"></a>Пример  
 Выполняет по требованию передачу набора сбора `Simple Collection Set`.  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_upload_collection_set @name = 'Simple Collection Set' ;  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)  
  
  

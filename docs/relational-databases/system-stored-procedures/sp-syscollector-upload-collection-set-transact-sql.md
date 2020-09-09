---
description: sp_syscollector_upload_collection_set (Transact-SQL)
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
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 13c21075035a499b21bede95f28e5bf4a00a9161
ms.sourcegitcommit: dd36d1cbe32cd5a65c6638e8f252b0bd8145e165
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/08/2020
ms.locfileid: "89534830"
---
# <a name="sp_syscollector_upload_collection_set-transact-sql"></a>sp_syscollector_upload_collection_set (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

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
`[ @collection_set_id = ] collection_set_id` Уникальный локальный идентификатор набора сбора. *collection_set_id* имеет **тип int** и должен иметь значение, если *Name* имеет значение null.  
  
`[ @name = ] 'name'` Имя набора элементов сбора. Аргумент *Name* имеет тип **sysname** и должен иметь значение, если *collection_set_id* имеет значение null.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Либо *collection_set_id* , либо *имя* должны иметь значение. Оба значения не могут иметь значение NULL.  
  
 Данная процедура может использоваться для начала передачи работающего набора сбора по требованию. Она может использоваться только для наборов сбора, настроенных для сбора и передачи данных в режиме с кэшированием. Это позволяет пользователю получить данные для анализа, не ожидая запланированной передачи.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных **dc_operator** (с разрешением EXECUTE).  
  
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
  
  

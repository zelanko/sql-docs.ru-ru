---
title: "sp_adjustpublisheridentityrange (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: language-reference
applies_to: SQL Server
f1_keywords:
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords: sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
caps.latest.revision: "28"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: c2f0214309eb060bbc02c7c05bf5243444ed5796
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="spadjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Настраивает диапазон идентификаторов для публикации и перераспределяет новые диапазоны на основе порогового значения публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@publication=**] **"***публикации***"**  
 Имя публикации, в которой повторно размещается диапазон идентификаторов. *Публикация* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_name=**] **"***table_name***"**  
 Имя таблицы, в которой повторно размещается диапазон идентификаторов. *имя_таблицы* — **sysname**, значение по умолчанию NULL.  
  
 [  **@table_owner=**] **"***table_owner***"**  
 Владелец исходной таблицы на стороне издателя. *TABLE_OWNER* — **sysname**, значение по умолчанию NULL. Если *table_owner* не указан, используется имя текущего пользователя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_adjustpublisheridentityrange** используется во всех типах репликации.  
  
 Агент распространителя или агент слияния являются ответственными за автоматическое изменение границ диапазона идентификаторов публикаций, для которых включено автоматическое определение диапазона на основе пороговых значений. Однако если для какой-либо причине агент распространителя или агент слияния не был выполнен в течение заданного времени, а ресурс диапазона идентификаторов интенсивно потребляет пороговую точку, пользователи могут вызывать **sp_adjustpublisheridentityrange** Чтобы выделить новый диапазон значений для издателя.  
  
 При выполнении **sp_adjustpublisheridentityrange**, либо *публикации* или *table_name* должен быть указан. Если указаны оба или ни одного, возвращается ошибка.  
  
## <a name="permissions"></a>Permissions  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять **sp_adjustpublisheridentityrange**.  
  
## <a name="see-also"></a>См. также:  
 [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

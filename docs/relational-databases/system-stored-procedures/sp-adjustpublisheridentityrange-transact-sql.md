---
title: sp_adjustpublisheridentityrange (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adjustpublisheridentityrange_TSQL
- sp_adjustpublisheridentityrange
helpviewer_keywords:
- sp_adjustpublisheridentityrange
ms.assetid: 64f111fd-fb7d-4459-93f7-65f0f8dd7efe
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 399fe5322cb8cb5c3d20a486aac3baa810439ce7
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62959708"
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
`[ @publication = ] 'publication'` — Имя публикации, в которой размещается новые диапазоны идентификаторов. *Публикация* — **sysname**, значение по умолчанию NULL.  
  
`[ @table_name = ] 'table_name'` — Имя таблицы, в которой размещается новые диапазоны идентификаторов. *TABLE_NAME* — **sysname**, значение по умолчанию NULL.  
  
`[ @table_owner = ] 'table_owner'` Является владельцем таблицы на издателе. *TABLE_OWNER* — **sysname**, значение по умолчанию NULL. Если *table_owner* не указан, используется имя текущего пользователя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_adjustpublisheridentityrange** используется во всех типах репликации.  
  
 Агент распространителя или агент слияния являются ответственными за автоматическое изменение границ диапазона идентификаторов публикаций, для которых включено автоматическое определение диапазона на основе пороговых значений. Тем не менее, если для какой-либо причине агент распространителя или агент слияния не был выполнен в течение заданного времени, а ресурс диапазона идентификаторов были использованы во многом на пороговую точку, пользователи могут вызывать **sp_adjustpublisheridentityrange** Чтобы выделить новый диапазон значений для издателя.  
  
 При выполнении **sp_adjustpublisheridentityrange**, либо *публикации* или *table_name* должен быть указан. Если указаны оба или ни одного, возвращается ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера или **db_owner** предопределенной роли базы данных могут выполнять процедуру **sp_adjustpublisheridentityrange**.  
  
## <a name="see-also"></a>См. также  
 [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

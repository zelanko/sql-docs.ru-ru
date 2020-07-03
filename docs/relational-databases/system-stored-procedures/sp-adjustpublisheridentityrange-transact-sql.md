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
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: ac449d2437184695c4d5957fea0788ce40a176ed
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85875217"
---
# <a name="sp_adjustpublisheridentityrange-transact-sql"></a>sp_adjustpublisheridentityrange (Transact-SQL)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  Настраивает диапазон идентификаторов для публикации и перераспределяет новые диапазоны на основе порогового значения публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_adjustpublisheridentityrange [ [ @publication = ] 'publication' ]  
    [ , [ @table_name = ] 'table_name' ]  
    [ , [ @table_owner= ] 'table_owner' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'`Имя публикации, в которой перераспределяются новые диапазоны идентификаторов. Аргумент *publication* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_name = ] 'table_name'`Имя таблицы, в которой перераспределяются новые диапазоны идентификаторов. Аргумент *table_name* имеет тип **sysname**и значение по умолчанию NULL.  
  
`[ @table_owner = ] 'table_owner'`Владелец таблицы на издателе. Аргумент *table_owner* имеет тип **sysname**и значение по умолчанию NULL. Если параметр *table_owner* не указан, используется имя текущего пользователя.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Комментарии  
 **sp_adjustpublisheridentityrange** используется во всех типах репликации.  
  
 Агент распространителя или агент слияния являются ответственными за автоматическое изменение границ диапазона идентификаторов публикаций, для которых включено автоматическое определение диапазона на основе пороговых значений. Однако, если по какой-либо причине агент распространения или агент слияния не выполнялись в течение определенного периода времени, а ресурс диапазона идентификаторов интенсивно потребляет точку порогового значения, пользователи могут вызвать **sp_adjustpublisheridentityrange** , чтобы выделить новый диапазон значений для издателя.  
  
 При выполнении **sp_adjustpublisheridentityrange**необходимо указать либо *публикацию* , либо *table_name* . Если указаны оба или ни одного, возвращается ошибка.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** или предопределенной роли базы данных **db_owner** могут выполнять **sp_adjustpublisheridentityrange**.  
  
## <a name="see-also"></a>См. также  
 [Репликация столбцов идентификаторов](../../relational-databases/replication/publish/replicate-identity-columns.md)   
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

---
title: sp_helpdistributor_properties (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpdistributor_properties_TSQL
- sp_helpdistributor_properties
helpviewer_keywords:
- sp_helpdistributor_properties
ms.assetid: ee267724-3244-49eb-84c9-f38dbefdd639
author: stevestein
ms.author: sstein
ms.openlocfilehash: e4cacb78e797583dbd45954f09c89a774c381966
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68770918"
---
# <a name="sp_helpdistributor_properties-transact-sql"></a>Хранимая процедура sp_helpdistributor_properties (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Возвращает свойства распространителя. Эта хранимая процедура выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helpdistributor_properties   
```  
  
## <a name="result-set"></a>Результирующий набор  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**heartbeat_interval**|**int**|Максимальное количество минут, в течение которых агент может выполняться без ведения журнала сообщений о процессе работы.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 **sp_helpdistributor_properties** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** , члены предопределенной роли базы данных **db_owner** или **replmonitor** в базе данных распространителя и пользователи из списка доступа к публикации (PAL) для публикации, использующей этот распространитель, могут выполнять **sp_helpdistributor_properties**.  
  
## <a name="see-also"></a>См. также:  
 [sp_changedistributor_property &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributor-property-transact-sql.md)  
  
  

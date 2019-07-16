---
title: sp_publisherproperty (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5c4ba291619ae756fa9803606eda4427a155ae39
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896492"
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает или изменяет свойства издателя для отличных [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей. Эта хранимая процедура выполняется на распространителе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [ **@publisher** =] **"***издателя***"**  
 Имя разнородного издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [ **@propertyname** =] **"***propertyname***"**  
 Имя устанавливаемого свойства. *PropertyName* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**xactsetbatching**|Показывает, группируются ли транзакции на издателе для последующей обработки в транзакционно целостные наборы, известные как наборы транзакций. Значение **включена** означает, что наборы транзакций могут создаваться, который используется по умолчанию. Значение **отключена** означает, что существующие наборы транзакций будут обработаны, но новые создаваться не будут созданы.|  
|**xactsetjob**|Разрешен ли запуск задания набора транзакций для создания набора транзакций. Значение **включена** означает, что периодически запускается задание набора транзакций для создания набора транзакций на издателе. Значение **отключена** означает, что наборы транзакций создаются только агентом чтения журнала, когда он запрашивает изменения с издателя.|  
|**xactsetjobinterval**|Интервал между запусками задания набора транзакций, в минутах.|  
  
 Когда *propertyname* опущен, возвращаются все устанавливаемые свойства.  
  
 [ **@propertyvalue** =] **"***propertyvalue***"**  
 Новое значение свойства. *propertyvalue* — **sysname**, со значением по умолчанию NULL. Когда *propertyvalue* опущен, текущее значение свойства возвращается.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|Возвращает следующие свойства публикации, которые могут быть установлены:<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**propertyvalue**|**sysname**|— Текущий параметр свойства в **propertyname** столбца.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_publisherproperty** используется в репликации транзакций для отличных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
 Только если *издателя* задан, результирующий набор включает текущие параметры для всех свойств, которые могут быть заданы.  
  
 Когда *propertyname* указано, только указанное свойство отображается в результирующем наборе.  
  
 Если указаны все аргументы, указанное свойство изменяется и результирующий набор не возвращается.  
  
 При изменении **xactsetjobinterval** свойство выполняется задание, необходимо перезапустить задание интервала нового вступили в силу.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на распространителе могут выполнять процедуру **sp_publisherproperty**.  
  
## <a name="see-also"></a>См. также  
 [Configure the Transaction Set Job for an Oracle Publisher](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  (Настройка задания для набора транзакции в издателе Oracle)  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

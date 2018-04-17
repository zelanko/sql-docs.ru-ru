---
title: sp_publisherproperty (Transact-SQL) | Документы Microsoft
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: language-reference
applies_to:
- SQL Server
f1_keywords:
- sp_publisherproperty
- sp_publisherproperty_TSQL
helpviewer_keywords:
- sp_publisherproperty
ms.assetid: 0ed1ebc1-a1bd-4aed-9f46-615c5cf07827
caps.latest.revision: 27
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 7446f507b688010f3044ff237d778f9b31b54fe8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="sppublisherproperty-transact-sql"></a>sp_publisherproperty (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Отображает или изменяет свойства издателя для не -[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей. Эта хранимая процедура выполняется на распространителе.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_publisherproperty [ @publisher = ] 'publisher'   
   [ , [ @propertyname = ] 'propertyname' ]   
   [ , [ @propertyvalue = ] 'propertyvalue' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [**@publisher** =] **"***издатель***"**  
 Имя разнородного издателя. *издатель* — **sysname**, не имеет значения по умолчанию.  
  
 [**@propertyname** =] **"***propertyname***"**  
 Имя устанавливаемого свойства. *PropertyName* — **sysname**, и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**xactsetbatching**|Показывает, группируются ли транзакции на издателе для последующей обработки в транзакционно целостные наборы, известные как наборы транзакций. Значение **включен** означает, что наборы транзакций могут создаваться, используемого по умолчанию. Значение **отключена** означает, что существующие наборы транзакций будут обработаны, но новые создаваться не создаются.|  
|**xactsetjob**|Разрешен ли запуск задания набора транзакций для создания набора транзакций. Значение **включен** означает периодически запускается задание набора транзакций для создания набора транзакций на издателе. Значение **отключена** означает, что наборы транзакций создаются только агентом чтения журнала, когда он запрашивает изменения с издателя.|  
|**xactsetjobinterval**|Интервал между запусками задания набора транзакций, в минутах.|  
  
 Когда *propertyname* пропущен, возвращаются все устанавливаемые свойства.  
  
 [**@propertyvalue** =] **"***propertyvalue***"**  
 Новое значение свойства. *propertyvalue* — **sysname**, значение по умолчанию NULL. Когда *propertyvalue* опущен, текущее значение свойства возвращается.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**propertyname**|**sysname**|Возвращает следующие свойства публикации, которые могут быть установлены:<br /><br /> **xactsetbatching**<br /><br /> **xactsetjob**<br /><br /> **xactsetjobinterval**|  
|**propertyvalue**|**sysname**|Текущее значение свойства в **propertyname** столбца.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 **sp_publisherproperty** используется в репликации транзакций для отличного[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателей.  
  
 Только если *издатель* задан, результирующий набор включает текущие параметры для всех свойств, которые могут быть установлены.  
  
 Когда *propertyname* указан, отображается только указанное свойство в результирующем наборе.  
  
 Если указаны все аргументы, указанное свойство изменяется и результирующий набор не возвращается.  
  
 При изменении **xactsetjobinterval** выполняется задание, необходимо перезапустить задание, новый интервал вступили в силу.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на распространителе могут выполнять **sp_publisherproperty**.  
  
## <a name="see-also"></a>См. также  
 [Configure the Transaction Set Job for an Oracle Publisher](../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)  (Настройка задания для набора транзакции в издателе Oracle)  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

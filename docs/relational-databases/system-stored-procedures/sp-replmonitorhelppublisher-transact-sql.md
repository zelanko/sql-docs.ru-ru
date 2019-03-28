---
title: sp_replmonitorhelppublisher (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replmonitorhelppublisher_TSQL
- sp_replmonitorhelppublisher
helpviewer_keywords:
- sp_replmonitorhelppublisher
ms.assetid: 171501fe-4b74-4647-96c3-7691c777e01b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f5f537dcb0f41c975ebbb7b5c6a27c2b2e306a09
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58532176"
---
# <a name="spreplmonitorhelppublisher-transact-sql"></a>sp_replmonitorhelppublisher (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения о текущем состоянии одного или нескольких издателей, связанных с распространителем. Эта хранимая процедура, используемая для наблюдения за репликацией, выполняется на распространителе в базе данных распространителя.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replmonitorhelppublisher [ [ @publisher = ] 'publisher' ]  
    [ , [ @refreshpolicy = ] refreshpolicy ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publisher = ] 'publisher'` — Имя издателя, состояние которого отслеживается. *издатель* — **sysname**, со значением по умолчанию NULL. Если задано значение NULL, то данные будут возвращены для всех издателей, которые используют этого распространителя.  
  
`[ @refreshpolicy = ] refreshpolicy` Только для внутреннего использования.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**издатель**|**sysname**|Имя издателя.|  
|**distribution_db**|**sysname**|Имя базы данных распространителя, применяемой данным издателем.|  
|**status**|**int**|Максимальное состояние всех агентов репликации, связанных с публикациями этого издателя. Может принимать одно из приведенных ниже значений:<br /><br /> **1** = запущен<br /><br /> **2** = выполнено успешно<br /><br /> **3** = выполняется<br /><br /> **4** = бездействует<br /><br /> **5** = Повтор<br /><br /> **6** = ошибка|  
|**Предупреждение**|**int**|Максимальный уровень предупреждений, выдаваемых подпиской, принадлежащей публикации этого издателя. Значение может быть результатом операции логического OR над одним или несколькими из следующих значений.<br /><br /> **1** = expiration — подписка на публикацию транзакций не была синхронизирована пороговым сроком хранения.<br /><br /> **2** = latency — время, необходимое для репликации данных транзакционного издателя на подписчик, превысило пороговое значение, в секундах.<br /><br /> **4** = mergeexpiration — подписка на публикацию слиянием не была синхронизирована пороговым сроком хранения.<br /><br /> **8** = mergefastrunduration — время, затраченное на завершение синхронизации подписки слиянием, превысило пороговое значение, в секундах, быстрое сетевое подключение.<br /><br /> **16** = mergeslowrunduration — время, затраченное на завершение синхронизации подписки слиянием через медленное или коммутируемое сетевое подключение превышает пороговое значение, в секундах.<br /><br /> **32** = mergefastrunspeed — скорость доставки строк во время синхронизации подписки слиянием не для поддержки пороговой, в строках в секунду, через быстрое сетевое подключение.<br /><br /> **64** = mergeslowrunspeed — скорость доставки строк во время синхронизации подписки слиянием не поддерживать пороговой, в строках в секунду, через медленное или коммутируемое сетевое подключение.|  
|**publicationcount**|**int**|Число публикаций, принадлежащих издателю.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_replmonitorhelppublisher** используется со всеми типами репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на распространителе или члены **db_owner** или **replmonitor** можно предопределенных ролей базы данных в базе данных распространителя выполнение **sp_replmonitorhelppublisher**.  
  
## <a name="see-also"></a>См. также  
 [Наблюдение за репликацией программным образом](../../relational-databases/replication/monitor/programmatically-monitor-replication.md)  
  
  

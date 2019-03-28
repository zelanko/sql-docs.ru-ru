---
title: sp_helppublication_snapshot (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helppublication_snapshot
- sp_helppublication_snapshot_TSQL
helpviewer_keywords:
- sp_helppublication_snapshot
ms.assetid: 97b4a7ae-40a5-4328-88f1-ff5d105bbb34
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0154f155c82554ba30ce71c9e7091fdc7565f587
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2019
ms.locfileid: "58526626"
---
# <a name="sphelppublicationsnapshot-transact-sql"></a>sp_helppublication_snapshot (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Возвращает сведения об агенте моментальных снимков для данной публикации. Эта хранимая процедура выполняется на издателе в базе данных публикации.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_helppublication_snapshot [ @publication = ] 'publication'  
    [ , [ @publisher = ] 'publisher' ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @publication = ] 'publication'` — Имя публикации. *Публикация* — **sysname**, не имеет значения по умолчанию.  
  
`[ @publisher = ] 'publisher'` Указывает, отличный от [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя. *издатель* — **sysname**, значение по умолчанию NULL.  
  
> [!NOTE]  
>  *издатель* не следует использовать при добавлении статьи к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя.  
  
## <a name="result-sets"></a>Результирующие наборы  
  
|Имя столбца|Тип данных|Описание|  
|-----------------|---------------|-----------------|  
|**идентификатор**|**int**|Идентификатор агента моментальных снимков.|  
|**name**|**nvarchar(100)**|Имя агента моментальных снимков.|  
|**publisher_security_mode**|**smallint**|Режим безопасности, используемый агентом при соединении с издателем, который может быть одним из следующих:<br /><br /> **0**  =  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] проверки подлинности<br /><br /> **1** = проверка подлинности Windows.|  
|**publisher_login**|**sysname**|Имя входа в систему, используемое при соединении с издателем.|  
|**publisher_password**|**nvarchar(524)**|По соображениям безопасности значение **\* \* \* \* \* \* \* \* \* \*** всегда возвращается.|  
|**job_id**|**uniqueidentifier**|Уникальный идентификатор задания агента.|  
|**job_login**|**nvarchar(512)**|— Это учетная запись Windows, под которой запускается агент моментальных снимков, которая возвращается в формате *домена*\\*username*.|  
|**job_password**|**sysname**|По соображениям безопасности значение **\* \* \* \* \* \* \* \* \* \*** всегда возвращается.|  
|**schedule_name**|**sysname**|Имя расписания, которое используется для этого задания агента.|  
|**frequency_type**|**int**|Частота, с которой агент выполняется по расписанию, может иметь одно из следующих значений.<br /><br /> **1** = один раз<br /><br /> **2** = по запросу<br /><br /> **4** = ежедневно<br /><br /> **8** = еженедельно<br /><br /> **16** = ежемесячно<br /><br /> **32** = ежемесячное расписание<br /><br /> **64** = автозапуск<br /><br /> **128** = повторять|  
|**frequency_interval**|**int**|День, когда агент выполняется, может иметь одно из следующих значений.<br /><br /> **1** = воскресенье<br /><br /> **2** = понедельник<br /><br /> **3** = Вторник<br /><br /> **4** = среда<br /><br /> **5** = четверг<br /><br /> **6** = Пятница<br /><br /> **7** = суббота<br /><br /> **8** = день<br /><br /> **9** = рабочие дни<br /><br /> **10** = выходные дни|  
|**frequency_subday_type**|**int**|— Тип, который определяет, как часто запускается агент, если *frequency_type* — **4** (ежедневно) и может принимать одно из следующих значений.<br /><br /> **1** = в указанное время<br /><br /> **2** = секунды<br /><br /> **4** = минуты<br /><br /> **8** = часы|  
|**frequency_subday_interval**|**int**|Число интервалов *frequency_subday_type* , которые проходят между запланированными выполнениями агента.|  
|**frequency_relative_interval**|**int**|Неделя, когда запускается агент в данном месяце при *frequency_type* — **32** (по месячному расписанию), и может принимать одно из следующих значений.<br /><br /> **1** = первый<br /><br /> **2** = второй<br /><br /> **4** = третий<br /><br /> **8** = четвертый<br /><br /> **16** = последний|  
|**frequency_recurrence_factor**|**int**|Число недель или месяцев между запланированными выполнениями агента.|  
|**active_start_date**|**int**|Дата, когда агент будет впервые выполнен, в формате ГГГГММДД.|  
|**active_end_date**|**int**|Дата, когда агент будет выполнен в последний раз, в формате ГГГГММДД.|  
|**active_start_time**|**int**|Время, когда агент будет впервые выполнен, в формате ЧЧММСС.|  
|**active_end_time**|**int**|Время, когда агент будет выполнен в последний раз, в формате ЧЧММСС.|  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Примечания  
 **sp_help_publication_snapshot** используется во всех типах репликации.  
  
## <a name="permissions"></a>Разрешения  
 Только члены **sysadmin** предопределенной роли сервера на издателе или члены **db_owner** предопределенной роли базы данных в базе данных публикации могут выполнять процедуру **sp_help_publication_snapshot** .  
  
## <a name="see-also"></a>См. также  
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [sp_addpublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addpublication-snapshot-transact-sql.md)   
 [sp_changepublication_snapshot &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-snapshot-transact-sql.md)   
 [sp_dropmergepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql.md)   
 [sp_droppublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-droppublication-transact-sql.md)  
  
  

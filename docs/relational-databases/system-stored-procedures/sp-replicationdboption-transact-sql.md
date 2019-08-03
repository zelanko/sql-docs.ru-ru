---
title: sp_replicationdboption (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_replicationdboption_TSQL
- sp_replicationdboption
helpviewer_keywords:
- sp_replicationdboption
ms.assetid: d021864e-3f21-4d1a-89df-6c1086f753bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ac51409db23f4b8eefb3616d5daf5ca43b3ab0f6
ms.sourcegitcommit: 728a4fa5a3022c237b68b31724fce441c4e4d0ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2019
ms.locfileid: "68771255"
---
# <a name="spreplicationdboption-transact-sql"></a>sp_replicationdboption (Transact-SQL)
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

  Устанавливает аргументы репликации указанной базы данных. Эта хранимая процедура выполняется на издателе или подписчике в любой базе данных.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_replicationdboption [ @dbname= ] 'db_name'   
        , [ @optname= ] 'optname'   
        , [ @value= ] 'value'   
    [ , [ @ignore_distributor= ] ignore_distributor ]  
    [ , [ @from_scripting = ] from_scripting ]  
```  
  
## <a name="arguments"></a>Аргументы  
 **[@dbname=** ] **'***dbname***'**  
 База данных, для которой устанавливаются параметры репликации. *db_name* имеет тип **sysname**и не имеет значения по умолчанию.  
  
 **[@optname=** ] **'***optname***'**  
 Параметр репликации базы данных, который должен быть включен или выключен. *optname* имеет тип **sysname**и может принимать одно из следующих значений.  
  
|Значение|Описание|  
|-----------|-----------------|  
|**Публикация слиянием**|База данных может использоваться для публикации слиянием.|  
|**отменить**|База данных может использоваться для других типов публикаций.|  
|**наблюдателя**|База данных является базой данных подписки.|  
|**Синхронизация с резервной копией**|База данных доступна для скоординированного создания резервных копий. Дополнительные сведения см. в разделе [Включение координированных резервных копий для репликации &#40;репликации транзакций программирование&#41;на языке Transact-SQL](../../relational-databases/replication/administration/enable-coordinated-backups-for-transactional-replication.md).|  
  
`[ @value = ] 'value'`Указывает, следует ли включить или отключить данный параметр базы данных репликации. **аргумент** *value* имеет тип sysname и может принимать **значение true** или **false**. Если это значение равно **false** и *optname* является **публикацией слиянием**, то подписки на опубликованную базу данных слияния также удаляются.  
  
`[ @ignore_distributor = ] ignore_distributor`Указывает, выполняется ли эта хранимая процедура без соединения с распространителем. *ignore_distributor* имеет **бит**и значение по умолчанию **0**. Это означает, что распространитель должен быть подключен к и обновлен с новым состоянием базы данных публикации. Значение **1** должно быть указано, только если распространитель недоступен и **sp_replicationdboption** используется для отключения публикации.  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 **sp_replicationdboption** используется в репликации моментальных снимков, репликации транзакций и репликации слиянием.  
  
 Эта процедура создает или удаляет определенные системные таблицы репликации, учетные записи безопасности и так далее в зависимости от указанного аргумента. Задает соответствующий бит категории в системной таблице **master. sysdatabases** и создает необходимые системные таблицы.  
  
 Для отключения публикации база данных публикации должна находиться в режиме «в сети». Если для базы данных публикации существует моментальный снимок, он должен быть удален перед отключением публикации. Моментальный снимок базы данных доступен только для чтения в виде копии базы данных вне сети и не относится к моментальному снимку репликации. Дополнительные сведения см. в разделе [Моментальные снимки базы данных (SQL Server)](../../relational-databases/databases/database-snapshots-sql-server.md).  
  
## <a name="permissions"></a>Разрешения  
 Только члены предопределенной роли сервера **sysadmin** могут выполнять **sp_replicationdboption**.  
  
## <a name="see-also"></a>См. также  
 [Настройка публикации и распространения](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Удаление публикации](../../relational-databases/replication/publish/delete-a-publication.md)   
 [Disable Publishing and Distribution](../../relational-databases/replication/disable-publishing-and-distribution.md)  (Отключение публикации и распространения)  
 [sys. sysdatabases &#40;TRANSACT-SQL&#41;](../../relational-databases/system-compatibility-views/sys-sysdatabases-transact-sql.md)   
 [Хранимые процедуры репликации (Transact-SQL)](../../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)  
  
  

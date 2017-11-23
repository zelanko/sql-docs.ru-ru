---
title: "sp_syscollector_update_collection_set (Transact-SQL) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collection_set_TSQL
- sp_syscollector_update_collection_set
dev_langs: TSQL
helpviewer_keywords:
- sp_syscollector_update_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 2dccc3cd-0e93-4e3e-a4e5-8fe89b31bd63
caps.latest.revision: "28"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 205e6dfd618bcf771fb035eafffc97578428b68f
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="spsyscollectorupdatecollectionset-transact-sql"></a>sp_syscollector_update_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Используется для изменения свойств или переименования определяемого пользователем набора элементов сбора.  
  
> [!WARNING]  
>  Если учетная запись Windows, настроенная как посредник, используется неинтерактивным или интерактивным пользователем, который еще не выполнил вход, то каталог профиля не будет создан, а создание промежуточного каталога будет невозможно. Вследствие этого при использовании учетной записи-посредника на контроллере домена необходимо указать интерактивную учетную запись, которая была использована хотя бы один раз, для того чтобы обеспечить создание каталога профиля.  
  
||  
|-|  
|**Область применения**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (с[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] до [текущей версии](http://go.microsoft.com/fwlink/p/?LinkId=299658)).|  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_update_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @new_name = ] 'new_name' ]  
    , [ [ @target = ] 'target' ]  
    , [ [ @collection_mode = ] collection_mode ]  
    , [ [ @days_until_expiration = ] days_until_expiration ]  
    , [ [ @proxy_id = ] proxy_id ]  
    , [ [ @proxy_name = ] 'proxy_name' ]  
    ,[ [ @schedule_uid = ] 'schedule_uid' ]  
    ,[ [ @schedule_name = ] 'schedule_uid' ]  
    , [ [ @logging_level = ] logging_level ]  
    , [ [ @description = ] 'description' ]  
```  
  
## <a name="arguments"></a>Аргументы  
 [  **@collection_set_id =** ] *collection_set_id, чтобы выделить*  
 Уникальный локальный идентификатор набора элементов сбора. *collection_set_id, чтобы выделить* — **int** и должен иметь значение, если *имя* имеет значение NULL.  
  
 [  **@name =** ] "*имя*"  
 Имя набора элементов сбора. *имя* — **sysname** и должен иметь значение, если *collection_set_id, чтобы выделить* имеет значение NULL.  
  
 [  **@new_name =** ] "*новое_имя*"  
 Новое имя для набора элементов сбора. *новое_имя* — **sysname**, и при использовании не может быть пустой строкой. *новое_имя* должно быть уникальным. Чтобы получить список имен текущего набора сбора, выполните запрос системного представления syscollector_collection_sets.  
  
 [  **@target =** ] "*целевой*"  
 Зарезервировано для последующего использования.  
  
 [  **@collection_mode =** ] *collection_mode*  
 Является типом коллекции данных для использования. *collection_mode* — **smallint** и может иметь одно из следующих значений:  
  
 0 — режим с кэшированием. Сбор и передача данных выполняются по отдельным расписаниям. Укажите кэшированный режим для непрерывного сбора.  
  
 1 — режим без кэширования. Сбор и передача данных выполняются по общему расписанию. Укажите некэшированный режим для нерегламентированного сбора или создания моментального снимка.  
  
 Если изменение с некэшированного на кэшированный (0), необходимо также указать либо *schedule_uid* или *schedule_name*.  
  
 [  **@days_until_expiration=** ] *days_until_expiration*  
 Число дней, в течение которых собранные данные хранятся в хранилище данных управления. *days_until_expiration* — **smallint**. *days_until_expiration* должно быть 0 или положительным целым числом.  
  
 [  **@proxy_id =** ] *proxy_id*  
 Уникальный идентификатор учетной записи-посредника агента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. *proxy_id* — **int**.  
  
 [  **@proxy_name =** ] "*proxy_name*"  
 Имя учетной записи-посредника. *proxy_name* — **sysname** и допускает значения NULL.  
  
 [  **@schedule_uid**  =] '*schedule_uid*"  
 Идентификатор GUID, указывающий на расписание. *schedule_uid* — **uniqueidentifier**.  
  
 Для получения *schedule_uid*, запрос системной таблицы sysschedules.  
  
 Когда *collection_mode* имеет значение 0, *schedule_uid* или *schedule_name* должен быть указан. Когда *collection_mode* имеет значение 1, *schedule_uid* или *schedule_name* учитывается, если указан.  
  
 [  **@schedule_name =** ] "*schedule_name*"  
 Имя расписания. *schedule_name* — **sysname** и допускает значения NULL. Если указано, *schedule_uid* должен иметь значение NULL. Для получения *schedule_name*, запрос системной таблицы sysschedules.  
  
 [  **@logging_level =** ] *logging_level*  
 Уровень ведения журнала. *LOGGING_LEVEL* — **smallint** с одним из следующих значений:  
  
 0 - Регистрировать сведения о выполнении и события служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], которые отслеживают:  
  
-   Запуск и остановку наборов сбора.  
  
-   Запуск и остановку пакетов.  
  
-   Сведения об ошибках.  
  
 1 — Ведение журнала на уровне 0, а также:  
  
-   Статистика выполнения.  
  
-   Ход непрерывно работающего сбора.  
  
-   Предупреждающие события от служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 2 - Ведениe журнала на уровне 1, а также запись подробных сведений о событиях служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 Значение по умолчанию для *logging_level* -1.  
  
 [  **@description =** ] "*описание*"  
 Описание набора элементов сбора. *Описание* — **nvarchar(4000)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (неуспешное завершение)  
  
## <a name="remarks"></a>Замечания  
 Функция sp_syscollector_update_collection_set должна выполняться в контексте системной базы данных msdb.  
  
 Либо *collection_set_id, чтобы выделить* или *имя* должен иметь значение, и не может иметь значение NULL. Чтобы получить эти значения, выполните запрос системного представления syscollector_collection_sets.  
  
 Если набор сбора выполняется, можно обновить только *schedule_uid* и *описание*. Чтобы остановить набор сбора, используйте [sp_syscollector_stop_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin или dc_operator (с разрешением EXECUTE). Хотя члены роли dc_operator могут выполнять эту хранимую процедуру, они могут менять не все свойства. Следующие свойства могут изменить только члены роли dc_admin:  
  
-   @new_name  
  
-   @target  
  
-   @proxy_id  
  
-   @description  
  
-   @collection_mode  
  
-   @days_until_expiration  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-renaming-a-collection-set"></a>A. Переименование набора элементов сбора  
 В следующем примере показано переименование определяемого пользователем набора элементов сбора.  
  
```  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_update_collection_set  
@name = N'Simple collection set test 1',  
@new_name = N'Collection set test 1 in cached mode';  
GO  
```  
  
### <a name="b-changing-the-collection-mode-from-non-cached-to-cached"></a>Б. Изменение режима сбора с некэшированного на кэшированный  
 В следующем примере режим сбора изменяется с некэшированного на кэшированный. Для этого изменения требуется указать идентификатор или имя расписания.  
  
```  
USE msdb;  
GO  
EXECUTE dbo.sp_syscollector_update_collection_set  
@name = N'Collection set test 1 in cached mode',  
@collection_mode = 0,  
@schedule_uid = 'C7022AF3-51B8-4011-B159-64C47C88FF70';  
-- alternatively, use @schedule_name.  
-- @schedule_name = N'CollectorSchedule_Every_15min;  
GO  
```  
  
### <a name="c-changing-other-collection-set-parameters"></a>В. Изменение других параметров набора элементов сбора  
 В следующем примере производится обновление различных свойств набора сбора «Simple collection set test 2».  
  
```  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_update_collection_set  
@name = N'Simple collection set test 2',  
@collection_mode = 1,  
@days_until_expiration = 5,  
@description = N'This is a test collection set that runs in noncached mode.',  
@logging_level = 0;  
GO  
```  
  
## <a name="see-also"></a>См. также:  
 [Системные хранимые процедуры (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40; Transact-SQL &#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)   
 [dbo.sysschedules &#40; Transact-SQL &#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  

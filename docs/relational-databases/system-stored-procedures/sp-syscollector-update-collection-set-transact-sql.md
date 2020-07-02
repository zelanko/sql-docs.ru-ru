---
title: sp_syscollector_update_collection_set (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collection_set_TSQL
- sp_syscollector_update_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 2dccc3cd-0e93-4e3e-a4e5-8fe89b31bd63
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 9385503d625c14932d520e4cf7390bf42612faff
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85639855"
---
# <a name="sp_syscollector_update_collection_set-transact-sql"></a>sp_syscollector_update_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/applies-to-version/sqlserver.md)]

  Используется для изменения свойств или переименования определяемого пользователем набора элементов сбора.  
  
> [!WARNING]  
>  Если учетная запись Windows, настроенная как посредник, используется неинтерактивным или интерактивным пользователем, который еще не выполнил вход, то каталог профиля не будет создан, а создание промежуточного каталога будет невозможно. Вследствие этого при использовании учетной записи-посредника на контроллере домена необходимо указать интерактивную учетную запись, которая была использована хотя бы один раз, для того чтобы обеспечить создание каталога профиля.  
  
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
`[ @collection_set_id = ] collection_set_id`Уникальный локальный идентификатор набора сбора. *collection_set_id* имеет **тип int** и должен иметь значение, если *Name* имеет значение null.  
  
`[ @name = ] 'name'`Имя набора элементов сбора. Аргумент *Name* имеет тип **sysname** и должен иметь значение, если *collection_set_id* имеет значение null.  
  
`[ @new_name = ] 'new_name'`Новое имя набора сбора. Аргумент *new_name* имеет тип **sysname**и, если он используется, не может быть пустой строкой. *new_name* должны быть уникальными. Чтобы получить список имен текущего набора сбора, выполните запрос системного представления syscollector_collection_sets.  
  
`[ @target = ] 'target'`Зарезервировано для будущего использования.  
  
`[ @collection_mode = ] collection_mode`Тип используемой коллекции данных. *collection_mode* имеет значение **smallint** и может иметь одно из следующих значений:  
  
 0 — режим с кэшированием. Сбор и передача данных выполняются по отдельным расписаниям. Укажите кэшированный режим для непрерывного сбора.  
  
 1 — режим без кэширования. Сбор и передача данных выполняются по общему расписанию. Укажите некэшированный режим для нерегламентированного сбора или создания моментального снимка.  
  
 При переходе от режима без кэширования в режим кэширования (0) необходимо также указать либо *schedule_uid* , либо *schedule_name*.  
  
`[ @days_until_expiration = ] days_until_expiration`Число дней, в течение которых собранные данные сохраняются в хранилище данных управления. *days_until_expiration* имеет **smallint**. *days_until_expiration* должно быть равно 0 или быть положительным целым числом.  
  
`[ @proxy_id = ] proxy_id`Уникальный идентификатор [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] учетной записи-посредника агента. *proxy_id* имеет **тип int**.  
  
`[ @proxy_name = ] 'proxy_name'`Имя прокси-сервера. *proxy_name* имеет тип **sysname** и допускает значение null.  
  
`[ @schedule_uid = ] 'schedule_uid'`Идентификатор GUID, указывающий на расписание. *schedule_uid* имеет тип **uniqueidentifier**.  
  
 Чтобы получить *schedule_uid*, запросите системную таблицу sysschedules.  
  
 Если *collection_mode* имеет значение 0, необходимо указать *schedule_uid* или *schedule_name* . Если параметр *collection_mode* имеет значение 1, *schedule_uid* или *schedule_name* игнорируется, если он указан.  
  
`[ @schedule_name = ] 'schedule_name'`Имя расписания. *schedule_name* имеет тип **sysname** и допускает значение null. Если указано, *schedule_uid* должны иметь значение null. Чтобы получить *schedule_name*, запросите системную таблицу sysschedules.  
  
`[ @logging_level = ] logging_level`Уровень ведения журнала. *LOGGING_LEVEL* имеет значение **smallint** с одним из следующих значений:  
  
 0 - Регистрировать сведения о выполнении и события служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], которые отслеживают:  
  
-   Запуск и остановку наборов сбора.  
  
-   Запуск и остановку пакетов.  
  
-   Сведения об ошибках.  
  
 1 — Ведение журнала на уровне 0, а также:  
  
-   Статистика выполнения.  
  
-   Ход непрерывно работающего сбора.  
  
-   Предупреждающие события от служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 2 - Ведениe журнала на уровне 1, а также запись подробных сведений о событиях служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 Значение по умолчанию для *LOGGING_LEVEL* равно 1.  
  
`[ @description = ] 'description'`Описание набора элементов сбора. *Описание* — **nvarchar (4000)**.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Функция sp_syscollector_update_collection_set должна выполняться в контексте системной базы данных msdb.  
  
 Либо *collection_set_id* , либо *имя* должны иметь значение, которое не может быть null. Чтобы получить эти значения, выполните запрос системного представления syscollector_collection_sets.  
  
 Если набор сбора выполняется, можно обновить только *schedule_uid* и *Description*. Чтобы прерывать набор сбора, используйте [sp_syscollector_stop_collection_set](../../relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql.md).  
  
## <a name="permissions"></a>Разрешения  
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
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [syscollector_collection_sets &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)   
 [dbo.sysрасписания &#40;&#41;Transact-SQL](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  

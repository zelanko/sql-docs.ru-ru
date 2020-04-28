---
title: sp_syscollector_create_collection_set (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collection_set_TSQL
- sp_syscollector_create_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_create_collection_set
ms.assetid: 69e9ff0f-c409-43fc-89f6-40c3974e972c
author: stevestein
ms.author: sstein
ms.openlocfilehash: e859ed97afdc3dfbb4e39a93b8691d044ceca37d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "68032638"
---
# <a name="sp_syscollector_create_collection_set-transact-sql"></a>sp_syscollector_create_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает новый набор элементов сбора. При помощи этой хранимой процедуры вы можете создать пользовательский набор элементов сбора для сбора данных.  
  
> [!WARNING]  
>  Если учетная запись Windows, настроенная как посредник, используется неинтерактивным или интерактивным пользователем, который еще не выполнил вход, то каталог профиля не будет создан, а создание промежуточного каталога будет невозможно. Вследствие этого при использовании учетной записи-посредника на контроллере домена необходимо указать интерактивную учетную запись, которая была использована хотя бы один раз, для того чтобы обеспечить создание каталога профиля.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_create_collection_set   
      [ @name = ] 'name'  
    , [ [ @target = ] 'target' ]  
    , [ [ @collection_mode = ] collection_mode ]  
    , [ [ @days_until_expiration = ] days_until_expiration ]  
    , [ [ @proxy_id = ] proxy_id ]  
    , [ [ @proxy_name = ] 'proxy_name' ]  
    , [ [ @schedule_uid = ] 'schedule_uid' ]  
    , [ [ @schedule_name = ] 'schedule_name' ]  
    , [ [ @logging_level = ] logging_level ]  
    , [ [ @description = ] 'description' ]  
    , [ @collection_set_id = ] collection_set_id OUTPUT   
    , [ [ @collection_set_uid = ] 'collection_set_uid' OUTPUT ]  
```  
  
## <a name="arguments"></a>Аргументы  
`[ @name = ] 'name'`Имя набора элементов сбора. Аргумент *Name* имеет тип **sysname** и не может быть пустой строкой или значением NULL.  
  
 *имя* должно быть уникальным. Чтобы получить список имен текущего набора сбора, выполните запрос системного представления syscollector_collection_sets.  
  
`[ @target = ] 'target'`Зарезервировано для будущего использования. *имя* имеет тип **nvarchar (128)** и значение по умолчанию NULL.  
  
`[ @collection_mode = ] collection_mode`Указывает способ, с помощью которого данные собираются и сохраняются. *collection_mode* имеет значение **smallint** и может иметь одно из следующих значений:  
  
 0 — режим с кэшированием. Сбор и передача данных выполняются по отдельным расписаниям. Укажите кэшированный режим для непрерывного сбора.  
  
 1 — режим без кэширования. Сбор и передача данных выполняются по общему расписанию. Укажите некэшированный режим для нерегламентированного сбора или создания моментального снимка.  
  
 Значение по умолчанию для *collection_mode* равно 0. Если *collection_mode* имеет значение 0, необходимо указать *schedule_uid* или *schedule_name* .  
  
`[ @days_until_expiration = ] days_until_expiration`Число дней, в течение которых собранные данные сохраняются в хранилище данных управления. *days_until_expiration* имеет значение **smallint** со значением по умолчанию 730 (два года). *days_until_expiration* должно быть равно 0 или быть положительным целым числом.  
  
`[ @proxy_id = ] proxy_id`Уникальный идентификатор учетной записи- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] посредника агента. *proxy_id* имеет **тип int** и значение по умолчанию NULL. Если указано, *proxy_name* должны иметь значение null. Чтобы получить *proxy_id*, запросите системную таблицу sysproxies. Предопределенная роль базы данных dc_admin должна иметь разрешение на доступ к посреднику. Дополнительные сведения см. [в статье создание агент SQL Server прокси-сервера](../../ssms/agent/create-a-sql-server-agent-proxy.md).  
  
`[ @proxy_name = ] 'proxy_name'`Имя учетной записи-посредника. *proxy_name* имеет тип **sysname** и значение по умолчанию NULL. Если указано, *proxy_id* должны иметь значение null. Чтобы получить *proxy_name*, запросите системную таблицу sysproxies.  
  
`[ @schedule_uid = ] 'schedule_uid'`Идентификатор GUID, указывающий на расписание. *schedule_uid* имеет значение **uniqueidentifier** со ЗНАЧЕНИЕМ по умолчанию NULL. Если указано, *schedule_name* должны иметь значение null. Чтобы получить *schedule_uid*, запросите системную таблицу sysschedules.  
  
 Если *collection_mode* имеет значение 0, необходимо указать *schedule_uid* или *schedule_name* . Если параметр *collection_mode* имеет значение 1, *schedule_uid* или *schedule_name* игнорируется, если он указан.  
  
`[ @schedule_name = ] 'schedule_name'`Имя расписания. *schedule_name* имеет тип **sysname** и значение по умолчанию NULL. Если указано, *schedule_uid* должны иметь значение null. Чтобы получить *schedule_name*, запросите системную таблицу sysschedules.  
  
`[ @logging_level = ] logging_level`Уровень ведения журнала. *LOGGING_LEVEL* имеет значение **smallint** с одним из следующих значений:  
  
 0 - регистрировать сведения о выполнении и события служб [!INCLUDE[ssIS](../../includes/ssis-md.md)], которые отслеживают:  
  
-   Запуск и остановку наборов сбора.  
  
-   Запуск и остановку пакетов.  
  
-   Сведения об ошибках.  
  
 1 — ведение журнала на уровне -0, а также:  
  
-   Статистика выполнения.  
  
-   Ход непрерывно работающего сбора.  
  
-   Предупреждающие события от служб [!INCLUDE[ssIS](../../includes/ssis-md.md)].  
  
 2 - ведение журнала на уровне -1, а также запись подробных сведений о событиях служб [!INCLUDE[ssIS](../../includes/ssis-md.md)]  
  
 Значение по умолчанию для *LOGGING_LEVEL* равно 1.  
  
`[ @description = ] 'description'`Описание набора элементов сбора. *Description* имеет тип **nvarchar (4000)** и значение по умолчанию NULL.  
  
`[ @collection_set_id = ] collection_set_id`Уникальный локальный идентификатор набора сбора. *collection_set_id* имеет **тип int** с OUTPUT и является обязательным.  
  
`[ @collection_set_uid = ] 'collection_set_uid'`Идентификатор GUID для набора сбора. *collection_set_uid* имеет тип **uniqueidentifier** с выходом со ЗНАЧЕНИЕМ по умолчанию NULL.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Remarks  
 Функция sp_syscollector_create_collection_set должна выполняться в контексте системной базы данных msdb.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin (с разрешением EXECUTE).  
  
## <a name="examples"></a>Примеры  
  
### <a name="a-creating-a-collection-set-by-using-default-values"></a>A. Создание набора элементов сбора при помощи значений по умолчанию  
 В следующем примере набор элементов сбора создается путем указания значений только для обязательных параметров. `@collection_mode` не требуется, но режим сбора (с кэшированием), используемый по умолчанию, требует указания идентификатора или имени расписания.  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
EXECUTE dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 1',  
    @description = N'This is a test collection set that runs in non-cached mode.',  
    @collection_mode = 1,  
    @collection_set_id = @collection_set_id OUTPUT;  
GO  
```  
  
### <a name="b-creating-a-collection-set-by-using-specified-values"></a>Б) Создание набора элементов сбора при помощи указанных значений  
 В следующем примере набор сбора создается путем указания значений для многих параметров.  
  
```  
USE msdb;  
GO  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier;  
SET @collection_set_uid = NEWID();  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'Simple collection set test 2',  
    @collection_mode = 0,  
    @days_until_expiration = 365,  
    @description = N'This is a test collection set that runs in cached mode.',  
    @logging_level = 2,  
    @schedule_name = N'CollectorSchedule_Every_30min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
```  
  
## <a name="see-also"></a>См. также:  
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [Создание пользовательского набора сбора, использующего тип сборщика «Универсальный запрос T-SQL» &#40;Transact-SQL&#41;](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)   
 [Хранимые процедуры сборщика данных &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)   
 [syscollector_collection_sets (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md)  
  
  

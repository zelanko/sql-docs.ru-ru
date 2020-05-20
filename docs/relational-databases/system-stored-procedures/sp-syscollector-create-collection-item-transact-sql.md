---
title: sp_syscollector_create_collection_item (Transact-SQL) | Документация Майкрософт
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_create_collection_item
- sp_syscollector_create_collection_item_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_create_collection_item
- data collector [SQL Server], stored procedures
ms.assetid: 60dacf13-ca12-4844-b417-0bc0a8bf0ddb
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: d597436277255441ad893215a3581580264d99a3
ms.sourcegitcommit: 4d3896882c5930248a6e441937c50e8e027d29fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/05/2020
ms.locfileid: "82810277"
---
# <a name="sp_syscollector_create_collection_item-transact-sql"></a>sp_syscollector_create_collection_item (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Создает элемент сбора в определяемом пользователем наборе сбора. Элемент сбора определяет, какие данные должны собираться, а также частоту их сбора.  
  
 ![Значок ссылки на раздел](../../database-engine/configure-windows/media/topic-link.gif "Значок ссылки на раздел") [Синтаксические обозначения в Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
sp_syscollector_create_collection_item   
      [ @collection_set_id = ] collection_set_id   
    , [ @collector_type_uid = ] 'collector_type_uid'  
    , [ @name = ] 'name'   
    , [ [ @frequency = ] frequency ]  
    , [ @parameters = ] 'parameters'  
    , [ @collection_item_id = ] collection_item_id OUTPUT  
```  
  
## <a name="arguments"></a>Аргументы  
 [ @collection_set_id =] *collection_set_id*  
 Уникальный локальный идентификатор набора элементов сбора. *collection_set_id* имеет **тип int**.  
  
 [ @collector_type_uid =] "*collector_type_uid*"  
 Идентификатор GUID, определяющий тип сборщика, используемый для этого элемента, *collector_type_uid* является **uniqueidentifier** и не имеет значения по умолчанию. Чтобы получить список типов сборщиков, выполните запрос системного представления syscollector_collector_types.  
  
 [ @name =] "*имя*"  
 Имя элемента сбора. Аргумент *Name* имеет тип **sysname** и не может быть пустой строкой или значением NULL.  
  
 *имя* должно быть уникальным. Чтобы получить список имен элементов текущего сбора, выполните запрос системного представления syscollector_collection_items.  
  
 [ @frequency =] *Частота*  
 Используется для указания времени (в секундах), определяющего, насколько часто этот элемент сбора собирает данные. параметр *Frequency* имеет **тип int**и значение по умолчанию 5. Минимальное значение, которое можно указать, составляет 5 секунд.  
  
 Если набор сбора настроен на режим без кэширования, частота не учитывается, поскольку этот режим предусматривает выполнение сбора данных и передачу по расписанию, указанному для набора сбора. Чтобы просмотреть режим сбора набора сбора, запросите [syscollector_collection_sets](../../relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql.md) системное представление.  
  
 [ @parameters =] "*Parameters*"  
 Входные параметры для типа сборщика. *Параметры* имеют **Формат XML** и значение по умолчанию NULL. Схема *параметров* должна соответствовать схеме параметров типа сборщика.  
  
 [ @collection_item_id =] *collection_item_id*  
 Уникальный идентификатор, определяющий элемент элементов набора. *collection_item_id* имеет **тип int** и имеет выходные данные.  
  
## <a name="return-code-values"></a>Значения кода возврата  
 **0** (успешное завершение) или **1** (сбой)  
  
## <a name="remarks"></a>Примечания  
 Функция sp_syscollector_create_collection_item должна выполняться в контексте системной базы данных msdb.  
  
 Набор сбора, в который добавляется элемент сбора, необходимо остановить перед созданием элемента сбора. Добавлять элементы сбора в системные наборы сбора невозможно.  
  
## <a name="permissions"></a>Разрешения  
 Для выполнения этой процедуры требуется членство в предопределенной роли базы данных dc_admin (с разрешением EXECUTE).  
  
## <a name="examples"></a>Примеры  
 В следующем примере элемент сбора создается на основе типа сборщика `Generic T-SQL Query Collector Type` и добавляется в набор сбора `Simple collection set test 2`. Чтобы создать указанный набор сбора, запустите пример б в [sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md).  
  
```  
USE msdb;  
GO  
DECLARE @collection_item_id int;  
DECLARE @collection_set_id int = (SELECT collection_set_id   
                                  FROM syscollector_collection_sets  
                                  WHERE name = N'Simple collection set test 2');  
DECLARE @collector_type_uid uniqueidentifier =   
    (SELECT collector_type_uid  
     FROM syscollector_collector_types  
     WHERE name = N'Generic T-SQL Query Collector Type');  
DECLARE @params xml =   
    CONVERT(xml, N'\<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
                <Value>SELECT * FROM sys.objects</Value>  
                <OutputTable>MyOutputTable</OutputTable>  
            </Query>  
            <Databases>   
                <Database> UseSystemDatabases = "true"   
                           UseUserDatabases = "true"  
                </Database>  
            </Databases>  
         \</ns:TSQLQueryCollector>');  
  
EXEC sp_syscollector_create_collection_item  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid,  
    @name = 'My custom TSQL query collector item',  
    @frequency = 6000,  
    @parameters = @params,  
    @collection_item_id = @collection_item_id OUTPUT;  
```  
  
## <a name="see-also"></a>См. также  
 [Системные хранимые процедуры &#40;&#41;Transact-SQL](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [Сбор данных](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_update_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql.md)   
 [sp_syscollector_delete_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql.md)   
 [syscollector_collector_types &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/syscollector-collector-types-transact-sql.md)   
 [sp_syscollector_create_collection_set &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md)   
 [syscollector_collection_items (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  

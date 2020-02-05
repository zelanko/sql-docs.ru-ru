---
title: Добавление элемента сбора в набор элементов сбора (T-SQL)
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection items [SQL Server]
- collection sets [SQL Server], adding items
ms.assetid: 9fe6454e-8c0e-4b50-937b-d9871b20fd13
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8b6a17bf6732221787bda5e34d42b01046b3f828
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "74055592"
---
# <a name="add-a-collection-item-to-a-collection-set-transact-sql"></a>Добавление элемента сбора в набор элементов сбора (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Добавить новый элемент сбора в существующий набор сбора можно с помощью хранимых процедур, предоставляемых вместе со сборщиком данных.  
  
 Выполните следующие шаги с помощью редактора запросов в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].  
  
### <a name="add-a-collection-item-to-a-collection-set"></a>Добавление элемента сбора в набор элементов сбора  
  
1.  Остановите набор сбора, в который необходимо добавить элемент, запустив хранимую процедуру **sp_syscollector_stop_collection_set** . Например, чтобы остановить набор сбора с именем «Тестовый набор сбора», выполните следующие инструкции:  
  
    ```sql  
    USE msdb  
    DECLARE @csid int  
    SELECT @csid = collection_set_id  
    FROM syscollector_collection_sets  
    WHERE name = 'Test Collection Set'  
    SELECT @csid  
    EXEC dbo.sp_syscollector_stop_collection_set @collection_set_id = @csid  
    ```  
  
    > [!NOTE]  
    >  Кроме того, набор сбора можно остановить с помощью обозревателя объектов среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Дополнительные сведения см. в разделе [Запуск или остановка набора элементов сбора](../../relational-databases/data-collection/start-or-stop-a-collection-set.md).  
  
2.  Объявите набор сбора, в который нужно добавить элемент сбора. В следующем коде представлен пример объявления идентификатора набора сбора.  
  
    ```sql  
    DECLARE @collection_set_id_1 int  
    SELECT @collection_set_id_1 = collection_set_id FROM [msdb].[dbo].[syscollector_collection_sets]  
    WHERE name = N'Test Collection Set'; -- name of collection set  
    ```  
  
3.  Объявление типа сборщика. В следующем коде представлен пример объявления типа сборщика «Универсальный запрос T-SQL».  
  
    ```sql  
    DECLARE @collector_type_uid_1 uniqueidentifier  
    SELECT @collector_type_uid_1 = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
       WHERE name = N'Generic T-SQL Query Collector Type';  
    ```  
  
     С помощью приведенного ниже кода можно получить список установленных типов сборщика:  
  
    ```sql  
    USE msdb  
    SELECT * from syscollector_collector_types  
    GO  
    ```  
  
4.  Запустите хранимую процедуру **sp_syscollector_create_collection_item** , чтобы создать элемент сбора. Необходимо объявить схему для элемента сбора, чтобы он был сопоставлен с требуемой схемой для сборщика нужного типа. В следующем примере используется схема «Универсальный запрос T-SQL».  
  
    ```sql  
    DECLARE @collection_item_id int;  
    EXEC [msdb].[dbo].[sp_syscollector_create_collection_item]   
    @name=N'OS Wait Stats', --name of collection item  
    @parameters=N'  
    <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
     <Query>  
      <Value>select * from sys.dm_os_wait_stats</Value>  
      <OutputTable>os_wait_stats</OutputTable>  
    </Query>  
    </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 60,  
    @collection_set_id = @collection_set_id_1, --- Provides the collection set ID number  
    @collector_type_uid = @collector_type_uid_1 -- Provides the collector type UID  
    SELECT @collection_item_id     
    ```  
  
5.  Перед запуском обновленного набора сбора запустите следующий запрос, чтобы убедиться, что новый элемент сбора был создан:  
  
    ```xaml  
    USE msdb  
    SELECT * from syscollector_collection_sets  
    SELECT * from syscollector_collection_items  
    GO  
    ```  
  
     Наборы сбора и их элементы сбора отображаются на вкладке **Результаты** .  
  
## <a name="see-also"></a>См. также:  
 [Создание пользовательского набора элементов сбора, использующего тип сборщика "Универсальный запрос T-SQL" (Transact-SQL)](../../relational-databases/data-collection/create-custom-collection-set-generic-t-sql-query-collector-type.md)   
 [Хранимые процедуры сборщика данных (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  

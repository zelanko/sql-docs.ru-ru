---
title: Использование некластеризованных индексов Columnstore | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e97aed3a5a4f5b49e482479b58928d2092a314f9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "62773795"
---
# <a name="using-nonclustered-columnstore-indexes"></a>Использование некластеризованных индексов columnstore
  Описывает основные задачи при использовании некластеризованного индекса columnstore в таблице [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .  
  
 Общие сведения об индексах columnstore см. в разделе [Columnstore Indexes Described](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Дополнительные сведения о кластеризованных индексах columnstore см. в разделе [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Содержание  
  
-   [Создание некластеризованного индекса Columnstore](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)  
  
-   [Изменение данных в некластеризованном индексе Columnstore](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)  
  
##  <a name="load"></a> Создание некластеризованного индекса Columnstore  
 Чтобы загрузить данные в некластеризованный индекс columnstore, сначала данные загружаются в стандартную таблицу rowstore сохраненную в виде кучи или кластеризованного индекса и воспользуйтесь [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) для создания Индекс ColumnStore.  
  
 ![Загрузка данных в индекс columnstore](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "загрузка данных в индекс columnstore")  
  
##  <a name="change"></a> Изменение данных в некластеризованном индексе Columnstore  
 После создания некластеризованного индекса columnstore в таблице нельзя непосредственно изменять данные в этой таблице. Запрос с инструкциями INSERT, UPDATE, DELETE или MERGE завершится сбоем и вернет сообщение об ошибке. Для добавления или изменения данных в таблице можно воспользоваться одним из следующих способов.  
  
-   Отключите индекс columnstore. Затем можно обновлять данные в таблице. Если отключить индекс columnstore, то можно перестроить его после окончания обновления данных. Пример:  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   Удалите индекс columnstore, обновить таблицу и затем заново создайте индекс columnstore с CREATE COLUMNSTORE INDEX. Пример:  
  
    ```  
    DROP INDEX mycolumnstoreindex ON mytable  
    -- update mytable --  
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;  
  
    ```  
  
-   Загрузка данных в промежуточную таблицу, не имеющую индекса columnstore. Создание индекса columnstore в промежуточной таблице. Переключение промежуточной таблицы в пустую секцию главной таблицы.  
  
-   Переключение секции из таблицы с индексом columnstore в пустую промежуточную таблицу. Если в промежуточной таблице имеется индекс columnstore, отключите индекс columnstore. Выполните все обновления. Постройте (или перестройте) индекс columnstore. Переключитесь с промежуточной таблицы обратно на (теперь пустую) секцию главной таблицы.  
  

  
  

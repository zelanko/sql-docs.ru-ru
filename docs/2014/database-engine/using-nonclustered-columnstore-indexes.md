---
title: Использование некластеризованных индексов Columnstore | Документация Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: table-view-index
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 4c341fb8-7cb1-4cab-921b-e80b751d6c19
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f32acde4b49b8b4b91c087fb66e41d4c2cf276ce
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37157025"
---
# <a name="using-nonclustered-columnstore-indexes"></a>Использование некластеризованных индексов columnstore
  Описывает основные задачи при использовании некластеризованного индекса columnstore в таблице [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Общие сведения об индексах columnstore см. в разделе [индексам ColumnStore](../relational-databases/indexes/columnstore-indexes-described.md).  
  
 Сведения о кластеризованных индексах columnstore см. в разделе [Using Clustered Columnstore Indexes](../relational-databases/indexes/indexes.md).  
  
## <a name="contents"></a>Содержание  
  
-   [Создание некластеризованного индекса Columnstore](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#load)  
  
-   [Изменение данных в некластеризованном индексе Columnstore](../../2014/database-engine/using-nonclustered-columnstore-indexes.md#change)  
  
##  <a name="load"></a> Создание некластеризованного индекса Columnstore  
 Чтобы загрузить данные в некластеризованный индекс columnstore, сначала данные загружаются в стандартную таблицу rowstore сохраненную в виде кучи или кластеризованного индекса и воспользуйтесь [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41; ](/sql/t-sql/statements/create-columnstore-index-transact-sql) для создания Индекс ColumnStore.  
  
 ![Загрузка данных в индекс columnstore](../../2014/database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "загрузка данных в индекс columnstore")  
  
##  <a name="change"></a> Изменение данных в некластеризованном индексе Columnstore  
 После создания некластеризованного индекса columnstore в таблице нельзя непосредственно изменять данные в этой таблице. Запрос с инструкциями INSERT, UPDATE, DELETE или MERGE завершится сбоем и вернет сообщение об ошибке. Для добавления или изменения данных в таблице можно воспользоваться одним из следующих способов.  
  
-   Отключите индекс columnstore. Затем можно обновлять данные в таблице. Если отключить индекс columnstore, то можно перестроить его после окончания обновления данных. Например:  
  
    ```  
    ALTER INDEX mycolumnstoreindex ON mytable DISABLE;  
    -- update mytable --  
    ALTER INDEX mycolumnstoreindex on mytable REBUILD  
    ```  
  
-   Удалите индекс columnstore, обновить таблицу и затем заново создайте индекс columnstore с CREATE COLUMNSTORE INDEX. Например:  
  
    ```  
    DROP INDEX mycolumnstoreindex ON mytable  
    -- update mytable --  
    CREATE NONCLUSTERED COLUMNSTORE INDEX mycolumnstoreindex ON mytable;  
  
    ```  
  
-   Загрузка данных в промежуточную таблицу, не имеющую индекса columnstore. Создание индекса columnstore в промежуточной таблице. Переключение промежуточной таблицы в пустую секцию главной таблицы.  
  
-   Переключение секции из таблицы с индексом columnstore в пустую промежуточную таблицу. Если в промежуточной таблице имеется индекс columnstore, отключите индекс columnstore. Выполните все обновления. Постройте (или перестройте) индекс columnstore. Переключитесь с промежуточной таблицы обратно на (теперь пустую) секцию главной таблицы.  
  

  
  

---
description: Создание запросов UNION (визуальные инструменты для баз данных)
title: Создание запросов UNION
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: b6d4d7618b3130e2b06d3efb8e9e2a35bc7ca0ee
ms.sourcegitcommit: 22dacedeb6e8721e7cdb6279a946d4002cfb5da3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/14/2020
ms.locfileid: "92038377"
---
# <a name="create-union-queries-visual-database-tools"></a>Создание запросов UNION (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Ключевое слово UNION позволяет включить результаты двух инструкций SELECT в одну результирующую таблицу. Все строки, возвращаемые каждой инструкцией SELECT, объединяются в результат выражения UNION. Примеры см. в разделе [Примеры использования инструкции SELECT (Transact-SQL)](../../t-sql/queries/select-examples-transact-sql.md).  
  
> [!NOTE]  
> Панель диаграмм может отображать только одно предложение SELECT. Следовательно, когда пользователь работает с запросом UNION, конструктор запросов скрывает панель «Табличные операции».  
  
### <a name="to-create-a-merged-select-query"></a>Создание объединенного запроса SELECT  
  
1.  Откройте запрос или создайте новый.  
  
2.  На панели SQL введите допустимое выражение UNION.  
  
    Следующий пример является допустимым выражением UNION.  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  В меню **Конструктор запросов** выберите пункт **Выполнить SQL** для запуска запроса.  
  
    Теперь запрос UNION отформатирован конструктором запросов.  
  
## <a name="see-also"></a>См. также  
[Поддерживаемые типы запросов](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Выполнение основных операций с запросами](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](../../t-sql/language-elements/set-operators-union-transact-sql.md)
---
title: Добавление производных таблиц в запросы (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4911b633fb6dcb2b40dc6d22828c0af53b0d2bda
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65088767"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a>Добавление производных таблиц в запросы (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Производная таблица — это результирующий набор, используемый в запросе в качестве исходных таблиц. Производную таблицу можно добавить в запрос на **панели диаграммы**.  
  
### <a name="to-add-a-derived-table-to-a-query"></a>Добавление в запрос производной таблицы  
  
1.  Откройте существующий запрос или создайте новый.  
  
2.  Щелкните правой кнопкой мыши **панель диаграммы** и выберите из контекстного меню пункт **Добавить новую производную таблицу**.  
  
    При этом добавляется новая таблица с именем derivedtbl_*N* , а в предложение FROM запроса добавляется инструкция SELECT для производной таблицы.  
  
## <a name="see-also"></a>См. также:  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[Создание запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/create-queries-visual-database-tools.md)  
[Открытие запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/open-queries-visual-database-tools.md)  
[SELECT (Transact-SQL)](https://msdn.microsoft.com/dc85caea-54d1-49af-b166-f3aa2f3a93d0)  
  

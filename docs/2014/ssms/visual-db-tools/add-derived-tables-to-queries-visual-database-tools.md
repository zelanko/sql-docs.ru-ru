---
title: Добавление производных таблиц в запросы (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [Visual Database Tools]
- joins [SQL Server], derived tables
- table joins [SQL Server]
- derived tables
ms.assetid: 05f1ba1d-465f-4e36-84bb-21b963c9b8f9
author: stevestein
ms.author: sstein
ms.openlocfilehash: 72169654b878f404950788b468bb6603035fd540
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85044449"
---
# <a name="add-derived-tables-to-queries-visual-database-tools"></a>Добавление производных таблиц в запросы (визуальные инструменты для баз данных)
  Производная таблица — это результирующий набор, используемый в запросе в качестве исходных таблиц. Производную таблицу можно добавить в запрос на **панели диаграммы**.  
  
### <a name="to-add-a-derived-table-to-a-query"></a>Добавление в запрос производной таблицы  
  
1.  Откройте существующий запрос или создайте новый.  
  
2.  Щелкните правой кнопкой мыши **панель диаграммы** и выберите из контекстного меню пункт **Добавить новую производную таблицу**.  
  
     При этом добавляется новая таблица с именем derivedtbl_*N* , а в предложение FROM запроса добавляется инструкция SELECT для производной таблицы.  
  
## <a name="see-also"></a>См. также:  
 [Выполнение основных операций с запросами &#40;визуальных инструментов для баз данных&#41;](visual-database-tools.md)   
 [Создание запросов &#40;визуальных инструментов для баз данных&#41;](create-queries-visual-database-tools.md)   
 [Открытие запросов &#40;визуальных инструментов для баз данных&#41;](open-queries-visual-database-tools.md)   
 [SELECT (Transact-SQL)](/sql/t-sql/queries/select-transact-sql)  
  
  

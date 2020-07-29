---
title: Создание псевдонимов таблиц
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: b89cec27a4c31b8165129fe4b3565ce6f448ac15
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999980"
---
# <a name="create-table-aliases-visual-database-tools"></a>Создание псевдонимов таблицы (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Псевдонимы облегчают работу с именами таблиц. Использование псевдонимов полезно в следующих случаях.  
  
-   Нужно сделать инструкцию на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md) более короткой и удобочитаемой.  
  
-   Запрос часто ссылается на имя таблицы (например, на квалификаторы имен столбцов), и при этом нужно сохранить определенную длину запроса. (В некоторых базах данных имеется ограничение на длину запроса).  
  
-   Обрабатывается несколько экземпляров одной таблицы (например при самосоединении), и нужно иметь возможность ссылаться на тот или иной экземпляр.  
  
Например, можно создать псевдоним `"e"` для имени таблицы `employee_information`, а затем ссылаться на нее, как `"e"`, по всему запросу.  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>Создание псевдонима таблицы или возвращающего табличное значение объекта  
  
1.  Добавьте таблицу или возвращающий табличное значение объект к запросу.  
  
2.  На **панели диаграммы**щелкните правой кнопкой нужный объект и выберите пункт **Свойства** в контекстном меню.  
  
3.  В окне **Свойства** введите псевдоним в поле **Псевдоним** .  
  
## <a name="see-also"></a>См. также:  
[Добавление таблиц в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

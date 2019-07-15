---
title: Создание псевдонимов таблиц (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 7b505c949c0e40150f992d024bb790bf06d9724e
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67690481"
---
# <a name="create-table-aliases-visual-database-tools"></a>Создание псевдонимов таблицы (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
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
  

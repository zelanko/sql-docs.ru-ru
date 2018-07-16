---
title: Создание псевдонимов таблиц (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- table aliases [SQL Server]
- aliases [SQL Server], tables
ms.assetid: 49e61e85-8abf-4ca7-8c70-7e9f8f1078bd
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a98f093964ae44dbb6bc301585d8a37e3bc3c296
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37327024"
---
# <a name="create-table-aliases-visual-database-tools"></a>Создание псевдонимов таблицы (визуальные инструменты для баз данных)
  Псевдонимы облегчают работу с именами таблиц. Использование псевдонимов полезно в следующих случаях.  
  
-   Нужно сделать инструкцию на [панели SQL](visual-database-tools.md) более короткой и удобочитаемой.  
  
-   Запрос часто ссылается на имя таблицы — например на квалификаторы имен столбцов, — и при этом нужно сохранить определенную длину запроса. (В некоторых базах данных имеется ограничение на длину запроса).  
  
-   Обрабатывается несколько экземпляров одной таблицы (например при самосоединении), и нужно иметь возможность ссылаться на тот или иной экземпляр.  
  
 Например можно создать псевдоним `"e"` для имени таблицы `employee`_`information`, а затем ссылаться на нее, как `"e"` , по всему запросу.  
  
### <a name="to-create-an-alias-for-a-table-or-table-valued-object"></a>Создание псевдонима таблицы или возвращающего табличное значение объекта  
  
1.  Добавьте таблицу или возвращающий табличное значение объект к запросу.  
  
2.  На **панели диаграммы**щелкните правой кнопкой нужный объект и выберите пункт **Свойства** в контекстном меню.  
  
3.  В окне **Свойства** введите псевдоним в поле **Псевдоним** .  
  
## <a name="see-also"></a>См. также  
 [Добавление таблиц в запросы &#40;визуальных инструментах баз данных&#41;](add-tables-to-queries-visual-database-tools.md)   
 [Результаты запросов сортировки и группирования &#40;визуальных инструментах баз данных&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Резюмирование результатов запросов &#40;визуальных инструментах баз данных&#41;](summarize-query-results-visual-database-tools.md)   
 [Выполнение основных операций с запросами (визуальные инструменты для баз данных)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  

---
title: Удаление таблиц из запросов (визуальные инструменты для базы данных) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 131a7e5ad9837c795b8a7f3c7360b84f8858177a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101003"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>Удаление таблиц из запросов (визуальные инструменты для базы данных)
  Из запроса можно удалить таблицу или любой возвращающий табличное значение объект.  
  
> [!NOTE]  
>  Удаление таблицы или возвращающего табличное значение объекта из текущего запроса не приводит к их удалению из базы данных. Дополнительные сведения об удалении таблицы из базы данных см. в разделе [удалить таблицы &#40;СУБД&#41;](../../relational-databases/tables/delete-tables-database-engine.md).  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>Удаление таблицы или табличного объекта  
  
-   На **панели диаграммы**выберите таблицу, представление, определяемую пользователем функцию, синоним или запрос и нажмите клавишу DELETE, либо щелкните объект правой кнопкой мыши и в контекстном меню выберите команду **Удалить** . Можно выбрать и одновременно удалить несколько объектов.  
  
     –или–  
  
-   Удалите все ссылки на объект на **панели SQL**.  
  
 При удалении таблицы или возвращающего табличное значение объекта конструктор запросов и представлений автоматически удаляет все включающие их соединения и ссылки на столбцы объектов на **панели SQL** и **панели критериев**. Однако если запрос содержит сложные выражения, включающие объект, то он может быть автоматически удален только после удаления всех ссылок на него.  
  
## <a name="see-also"></a>См. также  
 [Добавление таблиц в запросы &#40;визуальные средства базы данных&#41;](visual-database-tools.md)   
 [Создание псевдонимов таблицы &#40;визуальные средства базы данных&#41;](create-table-aliases-visual-database-tools.md)   
 [Укажите условия поиска &#40;визуальные средства базы данных&#41;](specify-search-criteria-visual-database-tools.md)   
 [Резюмирование результатов запросов &#40;визуальные средства базы данных&#41;](summarize-query-results-visual-database-tools.md)   
 [Выполнение основных операций с запросами (визуальные инструменты для баз данных)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  
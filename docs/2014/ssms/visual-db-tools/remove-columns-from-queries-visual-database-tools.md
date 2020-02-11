---
title: Удаление столбцов из запросов (визуальные инструменты для базы данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing columns
- queries [SQL Server], columns
- deleting columns
- dropping columns
ms.assetid: 6d9819b8-ee2f-4838-9713-c5e3ad37ab46
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 08230f1937d42247f8eeff09014f7727c6ebfe43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62659643"
---
# <a name="remove-columns-from-queries-visual-database-tools"></a>Удаление столбцов из запросов (визуальные инструменты для баз данных)
  Если столбец больше не нужен в запросе, то его можно удалить. При удалении столбца конструктор запросов и представлений удалит ссылки на него в списке выборки, установку сортировки, критерии поиска, **панель SQL**и все спецификации группирования.  
  
> [!NOTE]  
>  Если столбец нужно удалить только из выходных данных запроса Select, то это можно сделать без удаления столбца из запроса. Дополнительные сведения см. в разделе [Удаление столбцов из результатов запроса (визуальные инструменты для баз данных)](visual-database-tools.md).  
  
### <a name="to-remove-a-column-from-the-query"></a>Удаление столбца из запроса  
  
-   На **панели критериев**выберите строку сетки, содержащую нужный столбец, затем нажмите клавишу DELETE.  
  
     -или-  
  
-   Удалите все ссылки на столбец в [панели SQL](sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
 [Добавление столбцов в запросы &#40;визуальных инструментов для баз данных&#41;](add-columns-to-queries-visual-database-tools.md)   
 [Сортировка и Группировка результатов запроса &#40;визуальных инструментов для баз данных&#41;](sort-and-group-query-results-visual-database-tools.md)   
 [Суммировать результаты запроса &#40;визуальных инструментов для баз данных&#41;](summarize-query-results-visual-database-tools.md)   
 [Выполнение основных операций с запросами (визуальные инструменты для баз данных)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  

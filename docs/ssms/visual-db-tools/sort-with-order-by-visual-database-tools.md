---
title: Сортировка с помощью предложения ORDER BY (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- ORDER BY clause [Visual Database Tools]
ms.assetid: 459f5640-8058-4c24-97e7-7bbd6168bc39
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 07fb08547e8a114e9a580b1a13da8b1038b2f3ae
ms.sourcegitcommit: bb5484b08f2aed3319a7c9f6b32d26cff5591dae
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65099160"
---
# <a name="sort-with-order-by-visual-database-tools"></a>Произведение сортировки с помощью предложения ORDER BY (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Предложение ORDER BY позволяет сортировать результаты запроса по одному или нескольким столбцам. Его можно определить, выбрав параметры на панели «Подробности критериев».  
  
### <a name="to-sort-a-query-using-an-order-by-clause"></a>Для сортировки результатов запроса с помощью предложения ORDER BY:  
  
1.  Откройте запрос или создайте новый.  
  
2.  На [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)щелкните в столбце **Тип сортировки** строку, соответствующую столбцу, по которому нужно отсортировать результаты запроса.  
  
3.  В раскрывающемся списке выберите *По возрастанию* или *По убыванию* .  
  
> [!NOTE]  
> Очистка элемента **Тип сортировки** для столбца удаляет этот столбец из предложения ORDER BY.  
  
Обратите внимание, что во время работы с панелью критериев предложение UNION запроса изменяется в соответствии с последними действиями.  
  
> [!NOTE]  
> При сортировке результатов по нескольким столбцам в столбце **Порядок сортировки** укажите порядок, в котором будут просматриваться столбцы при сортировке. Дополнительные сведения см. в разделе **Как сортировать по нескольким столбцам в запросах**  
  
## <a name="see-also"></a>См. также:  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  

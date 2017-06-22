---
title: "Сортировка данных в порядке убывания или возрастания (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
caps.latest.revision: 3
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d287c698a353442efa64c9195702540e4b52f522
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a>отсортировать данные в порядке убывания и возрастания (визуальные инструменты для баз данных)
Результаты запроса можно отсортировать в возрастающем или убывающем порядке по одному или нескольким столбцам результирующего набора с помощью ключевых слов **ASC** или **DESC** в предложении **ORDER BY**.  
  
> [!NOTE]  
> Порядок сортировки частично определяется параметрами сортировки столбца. Очередность использования параметров сортировки можно изменить в диалоговом окне [Параметры сортировки](../../ssms/visual-db-tools/collation-dialog-box-visual-database-tools.md).  
  
Следующая инструкция подразумевает, что в конструкторе запросов и представлений открыт запрос, содержащий предложение ORDER BY для сортировки по одному или нескольким столбцам.  
  
### <a name="to-specify-or-change-the-order-in-which-results-are-sorted"></a>Указание или изменение порядка, в котором будут отсортированы результаты:  
  
1.  На [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)перейдите в поле **Тип сортировки** , соответствующее сортируемому столбцу.  
  
2.  Выберите **По возрастанию** или **По убыванию** , чтобы указать порядок сортировки для данного столбца.  
  
Обратите внимание, что во время работы с панелью критериев предложение UNION запроса изменяется в соответствии с последними действиями.  
  
> [!NOTE]  
> При сортировке результатов по нескольким столбцам в столбце «Порядок сортировки» укажите порядок, в котором будут просматриваться столбцы при сортировке. Дополнительные сведения см. в разделе [Сортировка по нескольким столбцам в запросах (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-multiple-columns-in-queries-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  


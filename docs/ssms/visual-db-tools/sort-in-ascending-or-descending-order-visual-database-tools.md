---
title: Сортировка данных в порядке убывания или возрастания (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- descending sorts
- ascending sorts
ms.assetid: d61cc55b-9ee8-4ecf-a32f-6459ae43910b
author: markingmyname
ms.author: maghan
manager: jroth
ms.openlocfilehash: 0154016bfcc8d94b94166f11e8778bdb25114edc
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67681348"
---
# <a name="sort-in-ascending-or-descending-order-visual-database-tools"></a>отсортировать данные в порядке убывания и возрастания (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Результаты запроса можно отсортировать в возрастающем или убывающем порядке по одному или нескольким столбцам результирующего набора с помощью ключевых слов **ASC** или **DESC** в предложении **ORDER BY** .  
  
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
  

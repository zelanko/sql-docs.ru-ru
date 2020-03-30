---
title: Переупорядочение выходных столбцов
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- reordering output columns [SQL Server]
- output columns [SQL Server]
ms.assetid: 76462885-de4a-4290-a26b-90696d3671f4
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 33739ef70de87ece117d57a9091dda83d60138fb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75255189"
---
# <a name="reorder-output-columns-visual-database-tools"></a>Переупорядочение выходных столбцов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Порядком, в соответствии с которым столбцы данных добавляются в запрос Select, определяется порядок, в котором они будут представлены в результатах. Первый столбец, добавляемый в запрос, в результатах располагается в крайней левой позиции, второй добавляемый в запрос столбец следует за ним и т. д.  
  
При создании запросов Update или Insert порядок добавления столбцов влияет на порядок обработки данных.  
  
Переупорядочивая столбцы, можно изменять местоположение столбца данных в результирующем наборе или порядок его использования.  
  
### <a name="to-reorder-columns-for-output"></a>Переупорядочение столбцов для вывода  
  
1.  На [панели критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)выберите строку, содержащую столбец, нажав кнопку выбора слева от строки.  
  
2.  Укажите кнопку выбора строки и перетащите строку в новое место.  
  
    -или-  
  
    Измените порядок имен столбцов на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
> [!TIP]  
> Можно добавить строку данных в определенную позицию на панель критериев, вставив пустую строку на панель критериев, а затем указав столбец данных для вставки. Дополнительные сведения см. в разделе [Добавление столбцов в запросы (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/add-columns-to-queries-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

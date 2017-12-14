---
title: "Исключение повторяющихся строк (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2c91c7023a10f0c1fa3eff598f40aa4372e8031d
ms.sourcegitcommit: b2d8a2d95ffbb6f2f98692d7760cc5523151f99d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2017
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Исключение повторяющихся строк (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Если необходимо, чтобы результирующий набор содержал лишь уникальные значения, можно исключить повторяющиеся значения из результирующего набора.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Удаление повторяющихся строк из результирующего набора  
  
1.  Щелкните правой кнопкой мыши фон панели диаграмм, а затем в контекстном меню выберите пункт **Свойства** .  
  
2.  В окне свойств щелкните **Неповторяющиеся значения** и установите значение **Да**.  
  
    Конструктор запросов и представлений поместит ключевое слово DISTINCT перед списком отображаемых столбцов в инструкции SQL.  
  
    > [!NOTE]  
    > При использовании ключевого слова DISTINCT изменение результирующего набора на панели результатов может оказаться невозможным.  
  
## <a name="see-also"></a>См. также:  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  

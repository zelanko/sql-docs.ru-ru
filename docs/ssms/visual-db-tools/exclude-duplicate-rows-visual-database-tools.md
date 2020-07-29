---
title: Исключение повторяющихся строк
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 2f652c40278a44d4bbe068a441e08ffe610af002
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "86012161"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Исключение повторяющихся строк (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Если необходимо, чтобы результирующий набор содержал лишь уникальные значения, можно исключить повторяющиеся значения из результирующего набора.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Удаление повторяющихся строк из результирующего набора  
  
1.  Щелкните правой кнопкой мыши фон панели диаграмм, а затем в контекстном меню выберите пункт **Свойства** .  
  
2.  В окне свойств щелкните **Неповторяющиеся значения** и установите значение **Да**.  
  
    Конструктор запросов и представлений поместит ключевое слово DISTINCT перед списком отображаемых столбцов в инструкции SQL.  
  
    > [!NOTE]  
    > При использовании ключевого слова DISTINCT изменение результирующего набора на панели результатов может оказаться невозможным.  
  
## <a name="see-also"></a>См. также:  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/sort-and-group-query-results-visual-database-tools.md)  
  

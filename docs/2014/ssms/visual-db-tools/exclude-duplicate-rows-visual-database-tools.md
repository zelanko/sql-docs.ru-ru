---
title: Исключение повторяющихся строк (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- search criteria [SQL Server], excluding rows
- row duplicates [SQL Server]
- duplicate rows
- row excluded in search [SQL Server]
- result sets [SQL Server], duplicate values
- excluding rows
ms.assetid: ab35a363-421d-4665-946b-ae3f6397af50
caps.latest.revision: 10
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 017385370989983d37f045379de926d0ebbf333f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36195514"
---
# <a name="exclude-duplicate-rows-visual-database-tools"></a>Исключение повторяющихся строк (визуальные инструменты для баз данных)
  Если необходимо, чтобы результирующий набор содержал лишь уникальные значения, можно исключить повторяющиеся значения из результирующего набора.  
  
### <a name="to-exclude-duplicate-rows-from-the-result-set"></a>Удаление повторяющихся строк из результирующего набора  
  
1.  Щелкните правой кнопкой мыши фон панели диаграмм, а затем в контекстном меню выберите пункт **Свойства** .  
  
2.  В окне свойств щелкните **Неповторяющиеся значения** и установите значение **Да**.  
  
     Конструктор запросов и представлений поместит ключевое слово DISTINCT перед списком отображаемых столбцов в инструкции SQL.  
  
    > [!NOTE]  
    >  При использовании ключевого слова DISTINCT изменение результирующего набора на панели результатов может оказаться невозможным.  
  
## <a name="see-also"></a>См. также  
 [Укажите условия поиска &#40;визуальные средства базы данных&#41;](visual-database-tools.md)   
 [Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](sort-and-group-query-results-visual-database-tools.md)  
  
  
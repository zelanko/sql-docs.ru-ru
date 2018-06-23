---
title: Создание запросов полнотекстового поиска (визуальные инструменты для баз данных) | Документация Майкрософт
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
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: 12
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3963876ce326529fd2538adc2d303d218406a924
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101001"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)
  Чтобы определить строки, содержащие в данном столбце указанный текст, в полнотекстовом поиске используется предикат CONTAINS. Полнотекстовый поиск возможен только в тех столбцах, для которых существуют активные полнотекстовые индексы. При попытке использовать предложение CONTAINS со столбцом, для которого в данный момент нет активного полнотекстового индекса, будет возвращена ошибка. Дополнительные сведения о полнотекстовых индексах и предложении CONTAINS см. в разделе [Full-Text Search](../../relational-databases/search/full-text-search.md) и [CONTAINS &#40;Transact-SQL&#41;](/sql/t-sql/queries/contains-transact-sql).  
  
### <a name="to-create-a-full-text-search-query"></a>Создание запроса полнотекстового поиска  
  
1.  Откройте запрос с помощью обозревателя решений или создайте новый.  
  
2.  Чтобы провести полнотекстовой поиск в столбце, в предложении WHERE запроса используйте функцию CONTAINS.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые типы запросов &#40;визуальные средства базы данных&#41;](visual-database-tools.md)   
 [Проектировать запросы и представления инструкции &#40;визуальные средства базы данных&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Выполнение основных операций с запросами (визуальные инструменты для баз данных)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  

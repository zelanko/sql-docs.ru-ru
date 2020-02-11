---
title: Задание условий для групп (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- HAVING clause, query groups
- group query conditions [SQL Server]
ms.assetid: 269ad9c5-3261-4526-badf-7be3c869f229
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bc0f9319e4d598548111b44b1a10542773a7daa4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63049156"
---
# <a name="specify-conditions-for-groups-visual-database-tools"></a>Задание условий для групп (визуальные инструменты для баз данных)
  Группы, возвращаемые запросом, можно ограничить, задав условие для групп в целом с помощью предложения HAVING. Условие в приложении HAVING применяется после группировки и статистической обработки данных. Запрос возвращает только те группы, которые удовлетворяют условию.  
  
 Допустим, требуется посмотреть среднюю цену на все книги каждого издателя в таблице `titles` , если средняя цена превышает $10.00. В этом случае в предложении HAVING можно указать следующее условие: `AVG(price) > 10`.  
  
> [!NOTE]  
>  Иногда требуется исключить из групп отдельные строки перед применением условия на всю группу. Дополнительные сведения см. в разделе [Использование предложения HAVING и WHERE в одном запросе (визуальные инструменты для баз данных)](visual-database-tools.md).  
  
 Предложение HAVING может содержать сложные условия, соединенные операторами AND и OR. Дополнительные сведения об использовании операторов AND и OR в условиях поиска см. в разделе [Указание нескольких условий поиска для одного столбца (визуальные инструменты для баз данных)](specify-multiple-search-conditions-for-one-column-visual-database-tools.md).  
  
### <a name="to-specify-a-condition-for-a-group"></a>Указание условия для группы  
  
1.  Укажите группы для запроса. Дополнительные сведения см. в разделе [Группирование строк в результатах запроса (визуальные инструменты для баз данных)](group-rows-in-query-results-visual-database-tools.md).  
  
2.  Если она уже находится на [панели критериев](criteria-pane-visual-database-tools.md), добавьте столбец, лежащий в основе условия. (Чаще всего условие содержит столбец, который является столбцом группы или суммарным столбцом.) Столбец, который отсутствует в агрегатной функции или предложении GROUP BY, использовать нельзя.  
  
3.  В столбце **Фильтр** укажите условие, которое требуется применить к группе.  
  
     [конструктор запросов и представлений](query-and-view-designer-tools-visual-database-tools.md) автоматически добавит предложение HAVING в инструкцию на [панели SQL](sql-pane-visual-database-tools.md), как показано в следующем примере:  
  
    ```  
    SELECT pub_id, AVG(price)  
    FROM titles  
    GROUP BY pub_id  
    HAVING (AVG(price) > 10)  
  
    ```  
  
4.  Повторите шаги 2 и 3 для каждого дополнительного условия.  
  
## <a name="see-also"></a>См. также:  
 [Результаты запросов сортировки и группирования (визуальные инструменты для баз данных)](sort-and-group-query-results-visual-database-tools.md)  
  
  

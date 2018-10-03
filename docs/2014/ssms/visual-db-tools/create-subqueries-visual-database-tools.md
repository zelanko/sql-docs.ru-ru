---
title: Создание вложенных запросов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], subqueries
- nested queries
- subqueries [SQL Server], SQL pane
ms.assetid: 34f6b9b4-ca3a-4a4f-9594-36e513f1c547
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: bed294d5568f4d7218c24d029781284c6bde0bfb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48221684"
---
# <a name="create-subqueries-visual-database-tools"></a>Создание вложенных запросов (визуальные инструменты для баз данных)
  Результаты одного запроса можно использовать в качестве входных данных другого запроса. Результаты вложенного запроса можно использовать в качестве инструкции, использующей функцию IN( ), оператор EXISTS или предложение FROM.  
  
 Вложенный запрос можно ввести непосредственно на панели «SQL» или создать его путем вставки одного запроса в другой.  
  
### <a name="to-define-a-subquery-in-the-sql-pane"></a>Создание вложенного запроса на панели «SQL»  
  
1.  Создайте первичный запрос.  
  
2.  На панели "SQL" выберите инструкцию SQL и скопируйте запрос в буфер обмена с помощью команды **Копировать** .  
  
3.  Запустите новый запрос и вставьте первоначальный запрос в предложение WHERE или FROM нового запроса с помощью команды **Вставить** .  
  
     Например, есть две таблицы `products` и `suppliers`, и нужно создать запрос, отображающий все продукты поставщиков из Швеции. Чтобы найти всех шведских поставщиков, создайте первый запрос в таблице `suppliers` :  
  
    ```  
    SELECT supplier_id  
    FROM supplier  
    WHERE (country = 'Sweden')  
    ```  
  
     Скопируйте этот запрос в буфер обмена. С помощью таблицы `products` создайте второй запрос. Укажите, какие сведения о продуктах нужно получить:  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    ```  
  
     На панели «SQL» добавьте во второй запрос предложение WHERE, затем вставьте из буфера обмена первый запрос. Отделите первый запрос круглыми скобками, чтобы конечный результат выглядел следующим образом:  
  
    ```  
    SELECT product_id, supplier_id, product_name  
    FROM products  
    WHERE supplier_id IN  
       (SELECT supplier_id  
      FROM supplier  
      WHERE (country = 'Sweden'))  
    ```  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые типы запросов &#40;визуальных инструментах баз данных&#41;](visual-database-tools.md)   
 [Определение критериев поиска (визуальные инструменты для баз данных)](specify-search-criteria-visual-database-tools.md)  
  
  

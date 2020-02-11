---
title: Создание вложенных запросов (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- search criteria [SQL Server], subqueries
- nested queries
- subqueries [SQL Server], SQL pane
ms.assetid: 34f6b9b4-ca3a-4a4f-9594-36e513f1c547
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e68809c7551e3c6711fadd9973c472dcb4e90307
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "63270622"
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
  
## <a name="see-also"></a>См. также:  
 [Поддерживаемые типы запросов &#40;визуальных инструментов для баз данных&#41;](visual-database-tools.md)   
 [Определение критериев поиска (визуальные инструменты для баз данных)](specify-search-criteria-visual-database-tools.md)  
  
  

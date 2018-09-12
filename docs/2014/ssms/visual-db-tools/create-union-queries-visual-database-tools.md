---
title: Создание запросов на объединение (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
caps.latest.revision: 12
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 559da2f60b0764c6dad07d33e16362eb80daa49c
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43806800"
---
# <a name="create-union-queries-visual-database-tools"></a>Создание запросов UNION (визуальные инструменты для баз данных)
  Ключевое слово UNION позволяет включить результаты двух инструкций SELECT в одну результирующую таблицу. Все строки, возвращаемые каждой инструкцией SELECT, объединяются в результат выражения UNION. Примеры, см. в разделе [примеры использования инструкции SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-examples-transact-sql).  
  
> [!NOTE]  
>  Панель диаграмм может отображать только одно предложение SELECT. Следовательно, когда пользователь работает с запросом UNION, конструктор запросов скрывает панель «Табличные операции».  
  
### <a name="to-create-a-merged-select-query"></a>Создание объединенного запроса SELECT  
  
1.  Откройте запрос или создайте новый.  
  
2.  На панели SQL введите допустимое выражение UNION.  
  
     Следующий пример является допустимым выражением UNION.  
  
    ```  
    SELECT ProductModelID, Name  
    FROM Production.ProductModel  
    UNION  
    SELECT ProductModelID, Name   
    FROM dbo.Gloves;  
    ```  
  
3.  В меню **Конструктор запросов** выберите пункт **Выполнить SQL** для запуска запроса.  
  
     Теперь запрос UNION отформатирован конструктором запросов.  
  
## <a name="see-also"></a>См. также  
 [Поддерживаемые типы запросов &#40;визуальных инструментах баз данных&#41;](visual-database-tools.md)   
 [Проектирование запросов и представлений инструкции &#40;визуальных инструментах баз данных&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [Выполнение основных операций с запросами &#40;визуальных инструментах баз данных&#41;](perform-basic-operations-with-queries-visual-database-tools.md)   
 [ОБЪЕДИНЕНИЕ &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/set-operators-union-transact-sql)  
  
  

---
title: Создание запросов на объединение (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f91d925dbdb8805620fee3ebfc7a0cd29f1fee2e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47840212"
---
# <a name="create-union-queries-visual-database-tools"></a>Создание запросов UNION (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Ключевое слово UNION позволяет включить результаты двух инструкций SELECT в одну результирующую таблицу. Все строки, возвращаемые каждой инструкцией SELECT, объединяются в результат выражения UNION. Примеры см. в разделе [Примеры использования инструкции SELECT (Transact-SQL)](http://msdn.microsoft.com/9b9caa3d-e7d0-42e1-b60b-a5572142186c).  
  
> [!NOTE]  
> Панель диаграмм может отображать только одно предложение SELECT. Следовательно, когда пользователь работает с запросом UNION, конструктор запросов скрывает панель «Табличные операции».  
  
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
  
## <a name="see-also"></a>См. также:  
[Поддерживаемые типы запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](http://msdn.microsoft.com/607c296f-8a6a-49bc-975a-b8d0c0914df7)  
  

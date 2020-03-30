---
title: Создание запросов UNION
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- queries [SQL Server], types
- UNION queries
- Select query
- combining query results
- merged SELECT query [SQL Server]
ms.assetid: b5aafb1d-e4ed-4922-b790-56abc5ec551a
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 23d918da8b938322c478682ea499136d4bf97b05
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254206"
---
# <a name="create-union-queries-visual-database-tools"></a>Создание запросов UNION (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Ключевое слово UNION позволяет включить результаты двух инструкций SELECT в одну результирующую таблицу. Все строки, возвращаемые каждой инструкцией SELECT, объединяются в результат выражения UNION. Примеры см. в разделе [Примеры использования инструкции SELECT (Transact-SQL)](https://msdn.microsoft.com/9b9caa3d-e7d0-42e1-b60b-a5572142186c).  
  
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
[Поддерживаемые типы запросов](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Выполнение основных операций с запросами](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
[UNION (Transact-SQL)](https://msdn.microsoft.com/607c296f-8a6a-49bc-975a-b8d0c0914df7)
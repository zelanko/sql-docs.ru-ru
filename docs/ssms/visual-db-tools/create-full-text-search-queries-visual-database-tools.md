---
title: Создание запросов полнотекстового поиска
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: eb7029f81e784df63a283a4ef12766d5deb97d37
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254347"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Чтобы определить строки, содержащие в данном столбце указанный текст, в полнотекстовом поиске используется предикат CONTAINS. Полнотекстовый поиск возможен только в тех столбцах, для которых существуют активные полнотекстовые индексы. При попытке использовать предложение CONTAINS со столбцом, для которого в данный момент нет активного полнотекстового индекса, будет возвращена ошибка. Дополнительные сведения о полнотекстовых индексах и предложении CONTAINS см. в разделах [Полнотекстовый поиск (SQL Server)](../../relational-databases/search/full-text-search.md) и [CONTAINS (Transact-SQL)](https://msdn.microsoft.com/996c72fc-b1ab-4c96-bd12-946be9c18f84).  
  
### <a name="to-create-a-full-text-search-query"></a>Создание запроса полнотекстового поиска  
  
1.  Откройте запрос с помощью обозревателя решений или создайте новый.  
  
2.  Чтобы провести полнотекстовой поиск в столбце, в предложении WHERE запроса используйте функцию CONTAINS.  
  
## <a name="see-also"></a>См. также:  
[Поддерживаемые типы запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

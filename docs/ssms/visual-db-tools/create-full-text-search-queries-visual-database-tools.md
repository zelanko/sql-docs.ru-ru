---
description: Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)
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
ms.reviewer: ''
ms.openlocfilehash: b861cf926bdbc43fda8986be44dacb5652196b7a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88369900"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Чтобы определить строки, содержащие в данном столбце указанный текст, в полнотекстовом поиске используется предикат CONTAINS. Полнотекстовый поиск возможен только в тех столбцах, для которых существуют активные полнотекстовые индексы. При попытке использовать предложение CONTAINS со столбцом, для которого в данный момент нет активного полнотекстового индекса, будет возвращена ошибка. Дополнительные сведения о полнотекстовых индексах и предложении CONTAINS см. в разделах [Полнотекстовый поиск (SQL Server)](../../relational-databases/search/full-text-search.md) и [CONTAINS (Transact-SQL)](https://msdn.microsoft.com/996c72fc-b1ab-4c96-bd12-946be9c18f84).  
  
### <a name="to-create-a-full-text-search-query"></a>Создание запроса полнотекстового поиска  
  
1.  Откройте запрос с помощью обозревателя решений или создайте новый.  
  
2.  Чтобы провести полнотекстовой поиск в столбце, в предложении WHERE запроса используйте функцию CONTAINS.  
  
## <a name="see-also"></a>См. также:  
[Поддерживаемые типы запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

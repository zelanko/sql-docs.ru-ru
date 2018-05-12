---
title: Создание запросов полнотекстового поиска (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2b6106cf3e0125d3ecab0f57f882d47db46bceb5
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>Создание запросов полнотекстового поиска (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
Чтобы определить строки, содержащие в данном столбце указанный текст, в полнотекстовом поиске используется предикат CONTAINS. Полнотекстовый поиск возможен только в тех столбцах, для которых существуют активные полнотекстовые индексы. При попытке использовать предложение CONTAINS со столбцом, для которого в данный момент нет активного полнотекстового индекса, будет возвращена ошибка. Дополнительные сведения о полнотекстовых индексах и предложении CONTAINS см. в разделах [Полнотекстовый поиск (SQL Server)](http://msdn.microsoft.com/en-us/a0ce315d-f96d-4e5d-b4eb-ff76811cab75) и [CONTAINS (Transact-SQL)](http://msdn.microsoft.com/en-us/996c72fc-b1ab-4c96-bd12-946be9c18f84).  
  
### <a name="to-create-a-full-text-search-query"></a>Создание запроса полнотекстового поиска  
  
1.  Откройте запрос с помощью обозревателя решений или создайте новый.  
  
2.  Чтобы провести полнотекстовой поиск в столбце, в предложении WHERE запроса используйте функцию CONTAINS.  
  
## <a name="see-also"></a>См. также:  
[Поддерживаемые типы запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[Разделы по конструированию запросов и представлений (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

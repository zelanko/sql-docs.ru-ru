---
title: "Создание запросов (визуальные инструменты для баз данных) | Документация Майкрософт"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: queries [SQL Server], creating
ms.assetid: 696a080d-848f-44d3-a918-e29bafaab85a
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 813673a5b992a27fe9d93f480024cb988136ab3a
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/17/2018
---
# <a name="create-queries-visual-database-tools"></a>Создание запросов (визуальные инструменты для баз данных)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Запросы позволяют получить данные из таблиц и представлений базы данных. Для создания запросов и работы с ними служит **Конструктор запросов и представлений**, который содержит четыре панели: [панель диаграммы](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md), [панель SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md), [панель критериев](../../ssms/visual-db-tools/criteria-pane-visual-database-tools.md)и [панель результатов](../../ssms/visual-db-tools/results-pane-visual-database-tools.md).  
  
### <a name="to-create-a-new-query"></a>Создание нового запроса  
  
1.  В **обозревателе объектов**разверните узел **Таблицы** для запрашиваемой базы данных. Щелкните нужную таблицу правой кнопкой мыши и выберите пункт **Открыть таблицу**.  
  
2.  Если в запрос нужно добавить еще какие-нибудь таблицы, в меню конструктора запросов выберите пункт **Добавить таблицу**.  
  
    > [!NOTE]  
    > Если панели **Диаграмма**, **SQL**, **Критерии**или **Результаты** отсутствуют, в меню конструктора запросов выберите **Область** и щелкните панель, которую нужно открыть.  
  
3.  В диалоговом окне **Добавление таблицы** выберите таблицы, к которым будет обращаться запрос, и для каждой из них нажмите кнопку **Добавить** .  
  
4.  Выбрав нужные таблицы, нажмите кнопку **Закрыть**.  
  
    Чтобы добавить новые таблицы, щелкните открытое место на панели **Диаграмма** правой кнопкой мыши и из контекстного меню выберите **Добавить таблицу**.  
  
5.  На **панели диаграммы**установите флажки в возвращающих табличное значение объектах для каждого столбца, к которому обращается запрос.  
  
6.  Чтобы выполнить запрос, в меню конструктора запросов выберите **Выполнить SQL** .  
  
При дальнейшем улучшении запроса можно изменить код SQL на **панели SQL** или выбрать такие параметры, как порядок сортировки или псевдонимы столбцов на **панели критериев**.  
  
## <a name="see-also"></a>См. также:  
[Сохранение запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/save-queries-visual-database-tools.md)  
[Типы запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/types-of-queries-visual-database-tools.md)  
[Определение критериев поиска (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Резюмирование результатов запросов (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

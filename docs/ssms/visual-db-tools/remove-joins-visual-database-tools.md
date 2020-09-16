---
description: Удаление соединений (визуальные инструменты для баз данных)
title: Удаление соединений
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: b13ffa676da9c96baa120ced607ca7607dea96d9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88497134"
---
# <a name="remove-joins-visual-database-tools"></a>Удаление соединений (визуальные инструменты для баз данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Если нежелательно, чтобы таблицы были соединены с помощью внутреннего или внешнего соединения, можно удалить это соединение между таблицами. Например, можно удалить соединение, автоматически созданное между двумя таблицами в [конструкторе запросов и представлений](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md) .  
  
> [!NOTE]  
> Удаление соединения из запроса не влияет на базовые связи, существующие в базе данных.  
  
Если две соединяемые таблицы являются частью запроса и все условия соединения между ними удаляются, то результирующий запрос становится пересечением этих таблиц, то есть перекрестным соединением (CROSS JOIN).  
  
### <a name="to-remove-a-join"></a>Удаление соединения  
  
-   На [панели диаграммы](../../ssms/visual-db-tools/diagram-pane-visual-database-tools.md)выберите удаляемую линию соединения и нажмите клавишу DELETE. Можно одновременно выбрать и удалить несколько линий соединений.  
  
Конструктор запросов и представлений удаляет линию соединения и изменяет инструкцию на [панели SQL](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также:  
[Автоматическое соединение таблиц (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-automatically-visual-database-tools.md)  
[Соединение таблиц вручную (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/join-tables-manually-visual-database-tools.md)  
[Запросы с соединениями (визуальные инструменты для баз данных)](../../ssms/visual-db-tools/query-with-joins-visual-database-tools.md)  
  

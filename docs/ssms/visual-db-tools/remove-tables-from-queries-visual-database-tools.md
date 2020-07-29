---
title: Удаление таблиц из запросов
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- deleting tables
- removing tables
- dropping tables
- queries [SQL Server], tables
ms.assetid: 8fea0b4f-99b7-4050-8d6f-a97ffb839619
author: markingmyname
ms.author: maghan
ms.reviewer: ''
ms.openlocfilehash: 2df3bd96d6fa2e398b4a4be1effefcc80f732df2
ms.sourcegitcommit: f3321ed29d6d8725ba6378d207277a57cb5fe8c2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/06/2020
ms.locfileid: "85999434"
---
# <a name="remove-tables-from-queries-visual-database-tools"></a>Удаление таблиц из запросов (визуальные инструменты для базы данных)
[!INCLUDE[SQL Server Azure SQL Database Synapse Analytics PDW ](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw.md)]
Из запроса можно удалить таблицу или любой возвращающий табличное значение объект.  
  
> [!NOTE]  
> Удаление таблицы или возвращающего табличное значение объекта из текущего запроса не приводит к их удалению из базы данных. Дополнительные сведения об удалении таблицы из базы данных см. в разделе [Как Удаление таблиц из базы данных](https://msdn.microsoft.com/ca6aa3e9-9885-44c3-bafc-aec441fd97ec).  
  
### <a name="to-remove-a-table-or-table-structured-object"></a>Удаление таблицы или табличного объекта  
  
-   На **панели диаграммы**выберите таблицу, представление, определяемую пользователем функцию, синоним или запрос и нажмите клавишу DELETE, либо щелкните объект правой кнопкой мыши и в контекстном меню выберите команду **Удалить** . Можно выбрать и одновременно удалить несколько объектов.  
  
    -или-  
  
-   Удалите все ссылки на объект на **панели SQL**.  
  
При удалении таблицы или возвращающего табличное значение объекта конструктор запросов и представлений автоматически удаляет все включающие их соединения и ссылки на столбцы объектов на **панели SQL** и **панели критериев**. Однако если запрос содержит сложные выражения, включающие объект, то он может быть автоматически удален только после удаления всех ссылок на него.  
  
## <a name="see-also"></a>См. также:  
[Добавление таблиц в запросы](../../ssms/visual-db-tools/add-tables-to-queries-visual-database-tools.md)  
[Создание псевдонимов таблиц](../../ssms/visual-db-tools/create-table-aliases-visual-database-tools.md)  
[Определение критериев поиска](../../ssms/visual-db-tools/specify-search-criteria-visual-database-tools.md)  
[Резюмирование результатов запросов](../../ssms/visual-db-tools/summarize-query-results-visual-database-tools.md)  
[Выполнение основных операций с запросами](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

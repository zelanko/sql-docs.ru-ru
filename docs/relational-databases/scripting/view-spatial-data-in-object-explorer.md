---
title: "Просмотр пространственных данных в обозревателе объектов | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8f01e7e2e0d13d80e3289f5da90b112f5806a6f
ms.sourcegitcommit: a0aa5e611a0e6ebb74ac1e2f613e8916dc7a7617
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2018
---
# <a name="view-spatial-data-in-object-explorer"></a>Просмотр пространственных данных в обозревателе объектов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] Окно **Пространственные результаты** в редакторе запросов содержит визуальные средства сопоставления для просмотра результатов запроса к пространственным данным в дополнение к данным, отображаемым в формате сетки в окне **Результаты**. Чтобы пространственные данные отображались в окне **Пространственные результаты** , результаты запроса должны содержать по крайней мере один столбец пространственных данных с данными геометрического или географического типа.  
  
### <a name="to-view-spatial-data-in-the-spatial-results-window"></a>Просмотр пространственных данных в окне «Пространственные результаты»  
  
1.  Перейдите на вкладку **Пространственные результаты** в редакторе запросов.  
  
    > [!NOTE]  
    >  Это окно будет недоступно, если в результаты запроса не входят пространственные данные или если задано возвращение результатов в виде текста.  
  
2.  Выберите в списке **Выберите пространственный столбец** столбец для просмотра. Если в таблице присутствует только один пространственный столбец, он будет выбираться в списке по умолчанию.  
  
3.  В списке **Выберите столбцы меток** выберите непространственный столбец для использования в качестве меток данных.  
  
4.  В списке **Выберите проекцию** выберите проекцию для географических данных. По умолчанию используется проекция Equirectangular. Также доступны проекции Mercator, Robinson и Bonne.  
  
    > [!NOTE]  
    >  Список**Выберите проекцию** недоступен, если пространственный столбец содержит геометрические данные.  
  
5.  Чтобы увеличить отображаемый размер сопоставленных элементов, передвиньте ползунок **Масштаб** . Для фигур-многоугольников метка будет видима только в случае, если фигура достаточно велика, чтобы вместить текст метки.  
  
## <a name="see-also"></a>См. также:  
 [Окно «Пространственные результаты»](../../relational-databases/scripting/spatial-results-window.md)   
 [Редактор запросов компонента Database Engine (среда SQL Server Management Studio)](../../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)   
 [Редакторы запросов и текста (SQL Server Management Studio)](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  

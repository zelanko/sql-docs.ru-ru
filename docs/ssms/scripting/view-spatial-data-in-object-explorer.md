---
title: Просмотр пространственных данных в обозревателе объектов | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 59cca562-e3f5-4257-b868-adcbcc0142cc
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 6437815a0251d3369d05ec479790752dd2aaf88e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821738"
---
# <a name="view-spatial-data-in-object-explorer"></a>Просмотр пространственных данных в обозревателе объектов
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  Окно **Пространственные результаты** в редакторе запросов содержит визуальные средства сопоставления для просмотра результатов запроса к пространственным данным в дополнение к данным, отображаемых в формате сетки в окне **Результаты** . Чтобы пространственные данные отображались в окне **Пространственные результаты** , результаты запроса должны содержать по крайней мере один столбец пространственных данных с данными геометрического или географического типа.  
  
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
  
  

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
manager: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3678c7d6ab6360f7fd546bcd2f36adc50c7294a5
ms.sourcegitcommit: 5d839dc63a5abb65508dc498d0a95027d530afb6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/09/2019
ms.locfileid: "67683296"
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
  
  

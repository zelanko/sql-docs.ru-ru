---
title: "Подготовка данных для отображения в области данных Табликса (построитель отчетов и службы SSRS) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
caps.latest.revision: 5
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 2d206770f54c16f08b958dbc06e7d613a960ad7a
ms.contentlocale: ru-ru
ms.lasthandoff: 08/09/2017

---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a>Подготовка данных для отображения в области данных табликса (построитель отчетов и службы SSRS)
  Область данных табликса отображает данные из набора данных. Существует возможность как просматривать все данные, полученные из набора данных, так и создавать фильтры, позволяющие просматривать подмножество этих данных. Можно также добавить условные выражения для заполнения пустых значений или изменить запрос к набору данных, включив в него столбцы, определяющие порядок сортировки для существующих столбцов.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a>Работа с пустыми значениями и значениями NULL в полях  
 Данные коллекции полей набора данных включают все значения, полученные из источника данных во время выполнения, в том числе значения NULL и пустые значения. Обычно эти два значения неотличимы. В большинстве случаев это приемлемо. Например, числовые агрегатные функции [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md) и [Avg](../../reporting-services/report-design/report-builder-functions-avg-function.md) не учитывают значения NULL. Дополнительные сведения см. в разделе [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
 Если значения NULL необходимо обрабатывать каким-либо иным образом, то можно воспользоваться условными выражениями или пользовательским кодом для замены NULL другим значением. Например, следующее выражение производит подстановку текста `Null` вместо значений NULL в столбце `[Size]`.  
  
```  
=IIF(Fields!Size.Value IS NOTHING,"Null",Fields!Size.Value)  
```  
  
 Дополнительные сведения об обработке значений NULL при получении данных из источника данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи запросов [!INCLUDE[tsql](../../includes/tsql-md.md)] см. в разделах «Значения NULL» и «Значения NULL и соединения» в документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в [электронной документации по SQL Server](http://go.microsoft.com/fwlink/?linkid=120955).  
  
## <a name="handling-null-field-names"></a>Обработка имен полей со значением NULL  
 Прекрасным решением будет проверка на значения NULL в выражении, поскольку в таком случае поле будет существовать в результирующем наборе запроса. В пользовательском коде придется во время выполнения проверять, существует ли поле в коллекции полей, возвращенных источником данных. Дополнительные сведения см. в разделе [Ссылки на коллекцию полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/built-in-collections-dataset-fields-collection-references-report-builder.md).  
  
## <a name="adding-a-sort-order-column"></a>Добавление столбца порядка сортировки  
 По умолчанию значения поля набора данных сортируются по алфавиту. Чтобы сортировка выполнялась в другом порядке, необходимо добавить в набор данных новый столбец, определяющий необходимый порядок сортировки области данных. Например, чтобы выполнить сортировку по полю `[Color]` таким образом, чтобы сначала шли белые и черные предметы, необходимо добавить столбец `[ColorSortOrder]`, показанный в следующем запросе.  
  
```  
SELECT ProductID, p.Name, Color,  
   CASE  
      WHEN p.Color = 'White' THEN 1  
      WHEN p.Color = 'Black' THEN 2  
      WHEN p.Color = 'Blue' THEN 3  
      WHEN p.Color = 'Yellow' THEN 4  
      ELSE 5  
   END As ColorSortOrder  
FROM Production.Product p  
```  
  
 Чтобы отсортировать область данных таблицы в соответствии с этим порядком сортировки, задайте для группы сведений выражение `=Fields!ColorSortOrder.Value`. Дополнительные сведения см. в разделе [Сортировка данных в области данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/sort-data-in-a-data-region-report-builder-and-ssrs.md).  
  
## <a name="see-also"></a>См. также:  
 [Коллекция полей набора данных &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Выражения &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Фильтр, группы и сортировка данных &#40; Построитель отчетов и службы SSRS &#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  

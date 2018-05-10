---
title: Подготовка данных для отображения в области данных табликса (построитель отчетов и службы SSRS) | Документы Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.component: report-design
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: fbb00dc6-7887-480c-b771-cab6fecb8dcc
caps.latest.revision: 5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e6b8f3672b21a43c87eb1dec7008593a93f3b850
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs"></a>Подготовка данных для отображения в области данных табликса (построитель отчетов и службы SSRS)
  Область данных табликса отображает данные из набора данных. Существует возможность как просматривать все данные, полученные из набора данных, так и создавать фильтры, позволяющие просматривать подмножество этих данных. Можно также добавить условные выражения для заполнения пустых значений или изменить запрос к набору данных, включив в него столбцы, определяющие порядок сортировки для существующих столбцов.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="working-with-nulls-and-blanks-in-field-values"></a>Работа с пустыми значениями и значениями NULL в полях  
 Данные коллекции полей набора данных включают все значения, полученные из источника данных во время выполнения, в том числе значения NULL и пустые значения. Обычно эти два значения неотличимы. В большинстве случаев это приемлемо. Например, числовые агрегатные функции [Sum](../../reporting-services/report-design/report-builder-functions-sum-function.md) и [Avg](../../reporting-services/report-design/report-builder-functions-avg-function.md) не учитывают значения NULL. Дополнительные сведения см. в разделах [Справочник по агрегатным функциям (построитель отчетов и службы SSRS)](../../reporting-services/report-design/report-builder-functions-aggregate-functions-reference.md).  
  
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
 [Коллекция полей набора данных (построитель отчетов и службы SSRS)](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Выражения (построитель отчетов и службы SSRS)](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Фильтрация, группирование и сортировка данных (построитель отчетов и службы SSRS)](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
  

---
title: "Импорт из многомерного источника данных (табличные службы SSAS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
caps.latest.revision: 13
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Импорт из многомерного источника данных (табличные службы SSAS)
  В качестве источника данных для табличной модели можно использовать базу данных куба служб Analysis Services. Чтобы импортировать данные из куба служб Analysis Services, необходимо указать запрос многомерных выражений для выбора данных.  
  
 Любые данные, которые содержатся в базе данных служб SQL Server Analysis Services, можно импортировать в модель. Можно извлечь все измерения или их часть, получить срезы и статистические выражения из куба, например суммы продаж по месяцам за текущий год и т. д. Однако необходимо иметь в виду, что все данные, импортируемые из куба, имеют плоский формат. Поэтому, если определить запрос, который получает меры с несколькими измерениями, данные будут импортированы для каждого измерения в отдельном столбце.  
  
 Кубы служб Analysis Services должны иметь версию SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].  
  
### Импортировать данные из куба служб Analysis Services  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
2.  На странице **Соединение с источником данных** выберите службы **Microsoft Analysis Services**и нажмите кнопку **Далее**.  
  
3.  Выполните шаги мастера импорта таблиц. На странице **Указание запроса MDX** можно указать запрос многомерных выражений. Для использования конструктора запросов многомерных выражений нажмите кнопку **Конструирование**на странице «Указание запроса MDX».  
  
## См. также  
 [Импорт данных (табличные службы SSAS)](../Topic/Import%20Data%20\(SSAS%20Tabular\).md)   
 [Поддерживаемые источники данных (табличные службы SSAS)](../../analysis-services/tabular-models/data-sources-supported-ssas-tabular.md)  
  
  
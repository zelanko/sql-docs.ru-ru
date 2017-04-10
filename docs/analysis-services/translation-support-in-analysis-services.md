---
title: "Поддержка параметров перевода в службах Analysis Services | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Business Intelligence Development Studio, переводы [службы Analysis Services]"
  - "переводы [службы Analysis Services], о переводах"
  - "переводы объектов [службы Analysis Services]"
  - "идентификаторы языка [службы Analysis Services]"
  - "переводы атрибутов [службы Analysis Services]"
  - "переводы [службы Analysis Services]"
ms.assetid: 018471e0-3c82-49ec-aa16-467fb58a6d5f
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 34
---
# Поддержка параметров перевода в службах Analysis Services
  В многомерные модели данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] вы можете включать несколько переводов заголовка или описания, чтобы предоставлять локализованные версии строк в зависимости от кода языка. В многомерных моделях переводы можно добавлять для имени базы данных, объектов куба и объектов измерений базы данных. В табличных моделях можно переводить названия и описания таблиц и столбцов.  
  
 При определении перевода внутри модели создаются метаданные и переведенный заголовок. Но чтобы локализованные строки отображались в клиентском приложении, следует задать для объекта свойство **Language** либо передать параметр **Culture** или **Locale Identifier** в строке подключения (например, параметр `LocaleIdentifier=1036` указывает, что нужно возвращать строки на французском языке).  
  
 Используйте **Locale Identifier** , если требуется поддерживать несколько одновременных переводов одного объекта на разных языках. Установка свойства **Language** работает, но оно также влияет на обработку и запросы, что может привести к непредвиденным последствиям. Установка свойства **Locale Identifier** — более оптимальный выбор, поскольку оно используется только для получения переведенных строк.  
  
 Перевод содержит код языка (LCID), переведенный заголовок для объекта (например, измерения или имени атрибута) и при необходимости привязку к столбцу, предоставляющую значения данных на целевом языке. Может быть несколько переводов, но для любого соединения можно использовать только один. Нет теоретического ограничения для количества переводов, которые можно внедрить в модель, но каждый перевод усложняет тестирование, а все переводы должны совместно использовать одинаковые параметры сортировки, поэтому при разработке решения учитывайте эти естественные ограничения.  
  
> [!TIP]  
>  Можно использовать клиентские приложения, например Excel, Management Studio и SQL Server Profiler, для возврата переведенных строк. Дополнительные сведения см. в разделе [Советы и рекомендации по глобализации (службы Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md).  
  
## Добавление переведенных метаданных в модель служб Analysis Services  
 Пошаговые инструкции приводятся в следующих статьях:  
  
-   [Переводы в табличных моделях (службы Analysis Services)](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [Переводы в многомерных моделях (службы Analysis Services)](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## См. также раздел  
 [Сценарии глобализации для служб Analysis Services](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Языки и параметры сортировки (службы Analysis Services)](../analysis-services/languages-and-collations-analysis-services.md)   
 [Задание или изменение параметров сортировки столбца](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Советы и рекомендации по глобализации (службы Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  
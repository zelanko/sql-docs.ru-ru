---
title: "Поддержка параметров перевода в службы Analysis Services | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Business Intelligence Development Studio, translations [Analysis Services]
- translations [Analysis Services], about translations
- object translations [Analysis Services]
- language identifiers [Analysis Services]
- attribute translations [Analysis Services]
- translations [Analysis Services]
ms.assetid: 018471e0-3c82-49ec-aa16-467fb58a6d5f
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 27715bc2c9333955931a1bc500a8267c0b1aa954
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="translation-support-in-analysis-services"></a>Поддержка параметров перевода в службах Analysis Services
  В многомерные модели данных [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] вы можете включать несколько переводов заголовка или описания, чтобы предоставлять локализованные версии строк в зависимости от кода языка. В многомерных моделях переводы можно добавлять для имени базы данных, объектов куба и объектов измерений базы данных. В табличных моделях можно переводить названия и описания таблиц и столбцов.  
  
 При определении перевода внутри модели создаются метаданные и переведенный заголовок. Но чтобы локализованные строки отображались в клиентском приложении, следует задать для объекта свойство **Language** либо передать параметр **Culture** или **Locale Identifier** в строке подключения (например, параметр `LocaleIdentifier=1036` указывает, что нужно возвращать строки на французском языке).  
  
 Используйте **Locale Identifier** , если требуется поддерживать несколько одновременных переводов одного объекта на разных языках. Установка свойства **Language** работает, но оно также влияет на обработку и запросы, что может привести к непредвиденным последствиям. Установка свойства **Locale Identifier** — более оптимальный выбор, поскольку оно используется только для получения переведенных строк.  
  
 Перевод содержит код языка (LCID), переведенный заголовок для объекта (например, измерения или имени атрибута) и при необходимости привязку к столбцу, предоставляющую значения данных на целевом языке. Может быть несколько переводов, но для любого соединения можно использовать только один. Нет теоретического ограничения для количества переводов, которые можно внедрить в модель, но каждый перевод усложняет тестирование, а все переводы должны совместно использовать одинаковые параметры сортировки, поэтому при разработке решения учитывайте эти естественные ограничения.  
  
> [!TIP]  
>  Можно использовать клиентские приложения, например Excel, Management Studio и SQL Server Profiler, для возврата переведенных строк. Дополнительные сведения см. в разделе [Советы и рекомендации по глобализации (службы Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md) .  
  
## <a name="how-to-add-translated-metadata-to-model-in-analysis-services"></a>Добавление переведенных метаданных в модель служб Analysis Services  
 Пошаговые инструкции приводятся в следующих статьях:  
  
-   [Переводы в табличных моделях (службы Analysis Services)](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [Переводы в многомерных моделях (службы Analysis Services)](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## <a name="see-also"></a>См. также раздел  
 [Сценарии глобализации для служб Analysis Services](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Языки и параметры сортировки &#40; Службы Analysis Services &#41;](../analysis-services/languages-and-collations-analysis-services.md)   
 [Задание или изменение параметров сортировки столбца](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Глобализация советы и лучшие методики &#40; Службы Analysis Services &#41;](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  


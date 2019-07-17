---
title: Поддержка параметров перевода в службах Analysis Services | Документация Майкрософт
ms.date: 01/09/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bd727b56649ce9ffc237575b0311db256ec9b2fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207420"
---
# <a name="translation-support-in-analysis-services"></a>Поддержка параметров перевода в службах Analysis Services
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

  В [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] моделей данных, можно внедрять несколько переводов заголовка или описания для предоставления строк, связанных с языком и региональными параметрами на основе идентификатора языкового стандарта (LCID). В многомерных моделях переводы можно добавлять для имени базы данных, объектов куба и объектов измерений базы данных. В табличных моделях можно переводить названия и описания таблиц и столбцов.  
  
 При определении перевода внутри модели создаются метаданные и переведенный заголовок. Но чтобы локализованные строки отображались в клиентском приложении, следует задать для объекта свойство **Language** либо передать параметр **Culture** или **Locale Identifier** в строке подключения (например, параметр `LocaleIdentifier=1036` указывает, что нужно возвращать строки на французском языке).  
  
 Используйте **Locale Identifier** , если требуется поддерживать несколько одновременных переводов одного объекта на разных языках. Установка свойства **Language** работает, но оно также влияет на обработку и запросы, что может привести к непредвиденным последствиям. Установка свойства **Locale Identifier** — более оптимальный выбор, поскольку оно используется только для получения переведенных строк.  
  
 Перевод содержит код языка (LCID), переведенный заголовок для объекта (например, измерения или имени атрибута) и при необходимости привязку к столбцу, предоставляющую значения данных на целевом языке. Может быть несколько переводов, но для любого соединения можно использовать только один. Нет теоретического ограничения для количества переводов, которые можно внедрить в модель, но каждый перевод усложняет тестирование, а все переводы должны совместно использовать одинаковые параметры сортировки, поэтому при разработке решения учитывайте эти естественные ограничения.  
  
> [!TIP]  
>  Клиентские приложения, например Excel, SQL Server Management Studio и SQL Server Profiler можно использовать для получения переведенных строк. Дополнительные сведения см. в разделе [Советы и рекомендации по глобализации (службы Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md) .  
  
## <a name="how-to-add-translated-metadata-to-model-in-analysis-services"></a>Добавление переведенных метаданных в модель служб Analysis Services  
 Пошаговые инструкции приводятся в следующих статьях:  
  
-   [Переводы в табличных моделях](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)  
  
-   [Переводы в многомерных моделях](../analysis-services/multidimensional-models/translations-in-multidimensional-models-analysis-services.md)  
  
## <a name="see-also"></a>См. также  
 [Сценарии глобализации для служб Analysis Services](../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [Языки и параметры сортировки (службы Analysis Services)](../analysis-services/languages-and-collations-analysis-services.md)   
 [Задание или изменение параметров сортировки столбца](../relational-databases/collations/set-or-change-the-column-collation.md)   
 [Советы и рекомендации по глобализации (службы Analysis Services)](../analysis-services/globalization-tips-and-best-practices-analysis-services.md)  
  
  

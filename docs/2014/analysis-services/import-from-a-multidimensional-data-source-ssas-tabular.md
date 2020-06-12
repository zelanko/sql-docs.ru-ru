---
title: Импорт из многомерного источника данных (табличные службы SSAS) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7f0793ea-a4c7-42e9-b722-2164a454ebca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3c062bab47317d121a2b1895742d70c79048413d
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544236"
---
# <a name="import-from-a-multidimensional-data-source-ssas-tabular"></a>Импорт из многомерного источника данных (табличные службы SSAS)
  В качестве источника данных для табличной модели можно использовать базу данных куба служб Analysis Services. Чтобы импортировать данные из куба служб Analysis Services, необходимо указать запрос многомерных выражений для выбора данных.  
  
 Любые данные, которые содержатся в базе данных служб SQL Server Analysis Services, можно импортировать в модель. Можно извлечь все измерения или их часть, получить срезы и статистические выражения из куба, например суммы продаж по месяцам за текущий год и т. д. Однако необходимо иметь в виду, что все данные, импортируемые из куба, имеют плоский формат. Поэтому, если определить запрос, который получает меры с несколькими измерениями, данные будут импортированы для каждого измерения в отдельном столбце.  
  
 Кубы служб Analysis Services должны иметь версию SQL Server 2005, SQL Server 2008, SQL Server 2008 R2, [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]или [!INCLUDE[ssSQL14](../includes/sssql14-md.md)].  
  
### <a name="to-import-data-from-an-analysis-services-cube"></a>Импортировать данные из куба служб Analysis Services  
  
1.  В среде [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]выберите пункт **Импорт из источника данных** в меню **Модель**.  
  
2.  На странице **Соединение с источником данных** выберите службы **Microsoft Analysis Services**и нажмите кнопку **Далее**.  
  
3.  Выполните шаги мастера импорта таблиц. На странице **Указание запроса MDX** можно указать запрос многомерных выражений. Для использования конструктора запросов многомерных выражений нажмите кнопку **Конструирование**на странице «Указание запроса MDX».  
  
## <a name="see-also"></a>См. также:  
 [Импорт данных &#40;табличные&#41;SSAS](import-data-ssas-tabular.md)   
 [Поддерживаемые источники данных (табличные службы SSAS)](tabular-models/data-sources-supported-ssas-tabular.md)  
  
  

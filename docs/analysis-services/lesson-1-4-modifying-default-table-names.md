---
title: "Изменение имен таблиц по умолчанию | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to: SQL Server 2016
ms.assetid: ddd97483-a76d-43c1-8b40-fc7cc57fb0c2
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 726cab6d57171e33d30ea61d397e54f7926cf00b
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="lesson-1-4---modifying-default-table-names"></a>Урок 1-4 - изменение имен таблиц по умолчанию
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]Можно изменить значение **FriendlyName** свойства для объектов в представлении источника данных, чтобы сделать их более понятными использовать.  
  
В следующей задаче будет изменено понятное имя каждой из таблиц в представлении источника данных посредством удаления из их имен префиксов**Dim**и**Fact**. Это сделает более понятными имена объектов куба и измерений, которые будут определены на следующем занятии.  
  
> [!NOTE]  
> Также в представлении источника данных можно присваивать понятные имена столбцам, определять вычисляемые столбцы, а также соединять таблицы и представления, чтобы сделать их более удобными в работе.  
  
### <a name="to-modify-the-default-name-of-a-table"></a>Изменение имени таблицы по умолчанию  
  
1.  На панели **Таблицы** **конструктора представлений источников данных**щелкните правой кнопкой мыши таблицу **FactInternetSales** и выберите пункт **Свойства**.  
  
2.  Если окно свойств не отображается в правой части окна Microsoft Visual Studio, нажмите кнопку **Автоматически скрывать** в строке заголовка окна свойств, чтобы окно оставалось видимым.  
  
    Когда окно свойств открыто, проще изменять свойства каждой таблицы в представлении источника данных. Если окно не закреплено в открытом состоянии с помощью кнопки **Автоматически скрывать** , оно будет закрыто, как только будет выбран другой объект на панели **Диаграмма** .  
  
3.  Измените свойство **FriendlyName** объекта **FactInternetSales** на ***InternetSales***.  
  
    Изменение будет применено, если щелкнуть вне ячейки свойства **FriendlyName** . На следующем занятии будет рассмотрено определение группы мер на основе этой таблицы фактов. Из-за сделанных на этом занятии изменений она будет называться не FactInternetSales, а InternetSales.  
  
4.  На панели **Таблицы** выберите таблицу **DimProduct** . В окне свойств задайте для свойства **FriendlyName** значение ***Продукт***.  
  
5.  Точно таким же образом измените значения свойства **FriendlyName** для всех оставшихся таблиц в представлении источника данных, удалив префикс**Dim**.  
  
6.  Затем нажмите кнопку **Автоматически скрывать** , чтобы снова скрыть окно свойств.  
  
7.  В меню **Файл** выберите пункт [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]Сохранить все **(или нажмите соответствующую кнопку на панели инструментов среды** ), чтобы сохранить изменения, внесенные в проект учебника по службам [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] . Если необходимо, здесь можно прервать работу с учебником, чтобы продолжить ее позже.  
  
## <a name="next-lesson"></a>Следующее занятие  
[Занятие 2. Определение и развертывание куба](../analysis-services/lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a>См. также:  
[Представления источников данных в многомерных моделях](../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)  
[Изменение свойств в представлении источника данных (службы Analysis Services)](../analysis-services/multidimensional-models/change-properties-in-a-data-source-view-analysis-services.md)  
  
  
  

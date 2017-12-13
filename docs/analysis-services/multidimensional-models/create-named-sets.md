---
title: "Для создания именованных наборов | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- calculations [Analysis Services], named sets
- named sets [Analysis Services]
- members [Analysis Services], named sets
ms.assetid: 03cf97a4-1a18-45f3-acb0-35123bd619be
caps.latest.revision: "31"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 0d8cc48ae6de8ffefb66960c2ecfed89dd2bc825
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="create-named-sets"></a>Создание именованных наборов
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Именованный набор — это набор элементов измерения или выражение набора, которые создаются для многократного использования, например в запросах многомерных выражений (MDX). Для создания именованных наборов может использоваться сочетание данных куба, арифметических операторов, чисел и функций. Например, можно создать именованный набор с именем Top Ten Factories, содержащий десять элементов измерения Factories с наибольшими значениями показателя Production. Затем набор Top Ten Factories можно использовать в запросах конечных пользователей. Например, конечный пользователь помещает набор Top Ten Factories на одну ось, а измерение меры, включая Production, — на другую ось. Дополнительные сведения см. в разделах [Вычисления в многомерных моделях](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md) и [Построение именованных наборов в многомерных выражениях](../../analysis-services/multidimensional-models/mdx/mdx-named-sets-building-named-sets.md).  
  
 Чтобы создать именованный набор, можно воспользоваться командой **Создать именованный набор** на вкладке **Вычисления** конструктора кубов. Эта команда может быть вызвана из меню **Куб** на панели инструментов вкладки **Вычисления** . Эта команда отображает форму для задания следующих параметров именованного набора.  
  
 **Название**  
 Выберите имя именованного набора. Это имя отображается при просмотре куба конечными пользователями.  
  
 **Выражение**  
 Укажите выражение, из которого получается именованный набор. Это выражение может быть записано на языке многомерных выражений. Выражение может содержать любой из следующих объектов:  
  
-   выражения данных, которые представляют компоненты куба, такие как измерения, уровни, меры и т. д.;  
  
-   арифметические операторы;  
  
-   числа.  
  
-   функции.  
  
 Можно скопировать или перетащить компоненты куба с вкладки **Метаданные** панели **Средства вычисления** в поле **Выражение** панели **Редактор форм именованных наборов** . Можно скопировать или перетащить функции с вкладки **Функции** панели **Средства вычисления** в поле **Выражение** панели **Редактор форм именованных наборов** .  
  
> [!IMPORTANT]  
>  При создании выражения набора с явным указанием имен для элементов набора следует заключить список элементов в фигурные скобки ({}).  
  
## <a name="see-also"></a>См. также раздел  
 [Вычисления в многомерных моделях](../../analysis-services/multidimensional-models/calculations-in-multidimensional-models.md)  
  
  

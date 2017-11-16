---
title: "Расширение OLAP через личные настройки | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
caps.latest.revision: 10
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 4a676978e37f257293b863786c3bcfae103ed4c4
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="extending-olap-through-personalizations"></a>Расширение OLAP через личные настройки
  Службы Analysis Services предоставляют множество встроенных функций для использования с языками многомерных выражений (MDX) и расширений интеллектуального анализа данных (DMX). Эти функции спроектированы, чтобы выполнять практически все, от стандартных статистических вычислений до прохода по элементам иерархии. Однако, как и в случае с любым другим сложным и надежным продуктом, возникает необходимость в дальнейшем расширении функциональности такого продукта.  
  
 Поэтому службы Analysis Services предоставляют возможность добавлять сборки и модули персонализации в экземпляр службы, чтобы удовлетворить потребности, не охватываемые стандартной функциональностью.  
  
## <a name="assemblies"></a>Сборки  
 Сборки позволяют расширять бизнес-функции многомерных выражений и расширений интеллектуального анализа данных. Требуемые функции формируются в виде библиотеки, например динамически подключаемой библиотеки (DLL), которая затем добавляется в качестве сборки к экземпляру служб Analysis Services или к базе данных служб Analysis Services. Общие методы в библиотеке затем открываются в виде пользовательских функций для многомерных выражений и выражений расширений интеллектуального анализа данных, их процедур, вычислений, действий и клиентских приложений.  
  
## <a name="personalized-extensions"></a>Модули персонализации  
 Модули персонализации служб SQL Server Analysis Services лежат в основе архитектуры подключаемых модулей. Модули персонализации служб Analysis Services — простое и элегантное изменение существующей архитектуры управляемых сборок. Модули доступны через объектную модель служб Analysis Services <xref:Microsoft.AnalysisServices.AdomdServer>, синтаксис многомерных выражений и наборы строк схемы.  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками многомерной модели](../../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Модули персонализации служб аналитики](../../../analysis-services/multidimensional-models/extending-olap/analysis-services-personalization-extensions.md)  
  
  


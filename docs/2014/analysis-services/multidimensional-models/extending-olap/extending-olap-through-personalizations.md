---
title: Расширение возможностей OLAP с помощью персонализаций | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
author: minewiskan
ms.author: owend
ms.openlocfilehash: 93669980e989b1cb11673f45c111de3609bbe920
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468949"
---
# <a name="extending-olap-through-personalizations"></a>Расширение OLAP через личные настройки
  Службы Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] предоставляют множество встроенных функций для использования в языках многомерных выражений (MDX) и расширений интеллектуального анализа данных (DMX). Эти функции спроектированы, чтобы выполнять практически все, от стандартных статистических вычислений до прохода по элементам иерархии. Однако, как и в случае с любым другим сложным и надежным продуктом, возникает необходимость в дальнейшем расширении функциональности такого продукта.  
  
 Поэтому службы Analysis Services предоставляют возможность добавлять сборки и модули персонализации в экземпляр службы, чтобы удовлетворить потребности, не охватываемые стандартной функциональностью.  
  
## <a name="assemblies"></a>Сборки  
 Сборки позволяют расширять бизнес-функции многомерных выражений и расширений интеллектуального анализа данных. Требуемые функции формируются в виде библиотеки, например динамически подключаемой библиотеки (DLL), которая затем добавляется в качестве сборки к экземпляру служб Analysis Services или к базе данных служб Analysis Services. Общие методы в библиотеке затем открываются в виде пользовательских функций для многомерных выражений и выражений расширений интеллектуального анализа данных, их процедур, вычислений, действий и клиентских приложений.  
  
## <a name="personalized-extensions"></a>Модули персонализации  
 Модули персонализации служб SQL Server Analysis Services лежат в основе архитектуры подключаемых модулей. Analysis Services расширений персонализации — это простое и элегантное изменение существующей архитектуры управляемой сборки. они доступны во всех Analysis Services объектной модели [Microsoft. AnalysisServices. того объектная AdomdServer](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120)) , СИНТАКСИСе многомерных выражений и наборах строк схемы.  
  
## <a name="see-also"></a>См. также  
 [Управление сборками многомерной модели](../multidimensional-model-assemblies-management.md)   
 [Модули персонализации служб Analysis Services](analysis-services-personalization-extensions.md)  
  
  

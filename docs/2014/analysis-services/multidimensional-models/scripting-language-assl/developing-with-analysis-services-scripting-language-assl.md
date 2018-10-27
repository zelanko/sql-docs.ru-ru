---
title: Разработка с помощью функций анализа служб языка сценариев (ASSL) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- Analysis Services Scripting Language
- ASSL
ms.assetid: ce9aca4d-b7ad-451e-bb7f-20c2b0c03f29
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1e12f03e96618a530c4f62f6a26cca904efeb43c
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/26/2018
ms.locfileid: "50145579"
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Разработка на языке ASSL (язык ASSL)
  Язык ASSL является расширением XML для аналитики, в котором добавлен язык определения объектов и командный язык для создания структур служб Analysis Services и управления этими структурами непосредственно на сервере. Язык ASSL можно применять в пользовательском приложении для обмена данными со службами Analysis Services по протоколу XMLA. Язык ASSL состоит из двух частей.  
  
-   Язык описания данных DDL, или язык определения объектов, который определяет и описывает экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], а также базы данных и объекты баз данных, находящихся в этом экземпляре.  
  
-   Командный язык, предназначенный для отправки экземпляру служб Analysis Services команд-действий, например `Create`, `Alter` или `Process`. Этот язык рассматривается в [XML для аналитики &#40;XMLA&#41; ссылку](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference).  
  
 Чтобы просмотреть код ASSL, описывающий многомерное решение в среде [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], можно использовать команду «Показать код» на уровне проекта. Также можно создать или изменить скрипт языка ASSL в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] с помощью редактора запросов XMLA. Построенные скрипты можно использовать для управления объектами и выполнения команд на сервере.  
  
## <a name="see-also"></a>См. также  
 [Объекты ASSL и характеристики объектов](assl-objects-and-object-characteristics.md)   
 [Обозначения в XML в ASSL](assl-xml-conventions.md)   
 [Источники данных и привязки (многомерные службы SSAS)](../data-sources-and-bindings-ssas-multidimensional.md)  
  
  

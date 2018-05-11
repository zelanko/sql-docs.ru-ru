---
title: Развертывание с помощью функций анализа служб язык сценариев (ASSL) | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 92e939c5ba180acdd0bd8509298ea1324a8414d7
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="developing-with-analysis-services-scripting-language-assl"></a>Разработка на языке ASSL (язык ASSL)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  Язык ASSL является расширением XML для аналитики, в котором добавлен язык определения объектов и командный язык для создания структур служб Analysis Services и управления этими структурами непосредственно на сервере. Язык ASSL можно применять в пользовательском приложении для обмена данными со службами Analysis Services по протоколу XMLA. Язык ASSL состоит из двух частей.  
  
-   Язык описания данных DDL, или язык определения объектов, который определяет и описывает экземпляр служб [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)], а также базы данных и объекты баз данных, находящихся в этом экземпляре.  
  
-   Командный язык, который отправляет команд-действий, таких как **создать**, **Alter**, или **процесс**, к экземпляру служб Analysis Services. Этот язык рассматривается в [XML для аналитики &#40;XMLA&#41; ссылки](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md).  
  
 Чтобы просмотреть код ASSL, описывающий многомерное решение в среде [!INCLUDE[ssBIDevStudio](../../../includes/ssbidevstudio-md.md)], можно использовать команду «Показать код» на уровне проекта. Также можно создать или изменить скрипт языка ASSL в среде [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] с помощью редактора запросов XMLA. Построенные скрипты можно использовать для управления объектами и выполнения команд на сервере.  
  
## <a name="see-also"></a>См. также  
 [Объекты ASSL и характеристики объектов](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-objects-and-object-characteristics.md)   
 [Соглашения XML языка ASSL](../../../analysis-services/multidimensional-models/scripting-language-assl/assl-xml-conventions.md)   
 [Источники данных и привязки & #40; Многомерные службы SSAS & #41;](../../../analysis-services/multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)  
  
  

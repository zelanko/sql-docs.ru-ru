---
title: "Определение обычной связи и ее свойств | Документы Microsoft"
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
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: "9"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 10025f3c362a0be45d782644ca36a41661e13c68
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Определение обычной связи и ее свойств
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]При определении нового измерения куба или новой группы мер, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли обычная связь и установить настройку использования измерения **регулярного**. Связь обычного измерения можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов.  
  
 При определении связи измерения куба с группой мер также указывается атрибут гранулярности для этой связи. Атрибут гранулярности определяет самый низкий уровень детализации, доступный в кубе для измерения, который обычно является ключевым атрибутом для этого измерения. Однако, в некоторых случаях может быть необходимо изменить размер гранул гранулярности конкретного измерения куба в конкретной группе мер. Например, может быть необходимо установить атрибут гранулярности для измерения «Время» равным атрибуту «Месяц», а не атрибуту «День», если используется группа мер «Квота на продажу» или «Бюджет». При указании того, что атрибут гранулярности не является ключевым атрибутом, необходимо гарантировать, что все остальные атрибуты в измерении непосредственно или косвенно связаны с этим другим атрибутом через связи атрибутов. Если это не так, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не смогут корректно выполнить статистическую обработку данных.  
  
  

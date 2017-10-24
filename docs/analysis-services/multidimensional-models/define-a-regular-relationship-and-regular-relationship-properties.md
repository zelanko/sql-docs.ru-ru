---
title: "Определение обычной связи и ее свойств | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
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
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 640b8197e37773249cb9afd53cbcad46d33754f9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Определение обычной связи и ее свойств
  При определении нового измерения куба или новой группы мер службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли обычная связь, и присвоить значение **Обычный**параметру, который определяет режим использования измерения. Связь обычного измерения можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов.  
  
 При определении связи измерения куба с группой мер также указывается атрибут гранулярности для этой связи. Атрибут гранулярности определяет самый низкий уровень детализации, доступный в кубе для измерения, который обычно является ключевым атрибутом для этого измерения. Однако, в некоторых случаях может быть необходимо изменить размер гранул гранулярности конкретного измерения куба в конкретной группе мер. Например, может быть необходимо установить атрибут гранулярности для измерения «Время» равным атрибуту «Месяц», а не атрибуту «День», если используется группа мер «Квота на продажу» или «Бюджет». При указании того, что атрибут гранулярности не является ключевым атрибутом, необходимо гарантировать, что все остальные атрибуты в измерении непосредственно или косвенно связаны с этим другим атрибутом через связи атрибутов. Если это не так, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не смогут корректно выполнить статистическую обработку данных.  
  
  


---
title: "Определение обычной связи и ее свойств | Документы Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
caps.latest.revision: 
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bc2ee7a49cddc8b5d6b0ce0905e2cbcd084a8897
ms.sourcegitcommit: 7519508d97f095afe3c1cd85cf09a13c9eed345f
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/15/2018
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a>Определение обычной связи и ее свойств
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
При определении нового измерения куба или новой группы мер службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] попытаются определить, существует ли обычная связь, и присвоить значение **Обычный**параметру, который определяет режим использования измерения. Связь обычного измерения можно просмотреть или отредактировать на вкладке **Использование измерений** конструктора кубов.  
  
 При определении связи измерения куба с группой мер также указывается атрибут гранулярности для этой связи. Атрибут гранулярности определяет самый низкий уровень детализации, доступный в кубе для измерения, который обычно является ключевым атрибутом для этого измерения. Однако, в некоторых случаях может быть необходимо изменить размер гранул гранулярности конкретного измерения куба в конкретной группе мер. Например, может быть необходимо установить атрибут гранулярности для измерения «Время» равным атрибуту «Месяц», а не атрибуту «День», если используется группа мер «Квота на продажу» или «Бюджет». При указании того, что атрибут гранулярности не является ключевым атрибутом, необходимо гарантировать, что все остальные атрибуты в измерении непосредственно или косвенно связаны с этим другим атрибутом через связи атрибутов. Если это не так, службы [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] не смогут корректно выполнить статистическую обработку данных.  
  
  

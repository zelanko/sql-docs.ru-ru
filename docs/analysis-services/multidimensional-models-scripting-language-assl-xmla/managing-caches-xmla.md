---
title: "Управление кэшами (XMLA) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
caps.latest.revision: "13"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6dad9f3bb8c577ea8fb975d4f8ba4eac054f0a3e
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2017
---
# <a name="managing-caches-xmla"></a>Управление кэшами (XMLA)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Можно использовать [ClearCache](../../analysis-services/xmla/xml-elements-commands/clearcache-element-xmla.md) в XML для аналитики (XMLA) для очистки кэша указанного измерения или секции. Очистка кэша вынуждает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] перестроение кэша для этого объекта.  
  
## <a name="specifying-objects"></a>Указание объектов  
 [Объекта](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md) свойство **ClearCache** команды может содержать ссылку объекта только для одного из следующих объектов. Если ссылка объекта указывает на объект, отличный от объекта из следующего списка, возникает ошибка:  
  
 База данных  
 Очищает кэш для всех измерений и секций, содержащихся в базе данных.  
  
 Измерение  
 Очищает кэш для указанного измерения.  
  
 Cube  
 Очищает кэш для всех секций, содержащихся в группе мер для куба.  
  
 Группа мер  
 Очищает кэш для всех секций, содержащихся в группе мер.  
  
 Секция  
 Очищает кэш для указанной секции.  
  
## <a name="see-also"></a>См. также:  
 [Разработка с использованием XMLA в службах Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

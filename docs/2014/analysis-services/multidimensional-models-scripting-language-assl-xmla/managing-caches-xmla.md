---
title: Управление кэшами (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdc5bcd2e0500749edfa298a871b6fec7243ddfb
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544988"
---
# <a name="managing-caches-xmla"></a>Управление кэшами (XMLA)
  Для очистки кэша указанного измерения или секции можно использовать команду [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) в XML для АНАЛИТИКИ (XMLA). Очистка кэша приводит [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] к перестроению кэша для этого объекта.  
  
## <a name="specifying-objects"></a>Указание объектов  
 Свойство [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) `ClearCache` команды может содержать ссылку на объект только для одного из следующих объектов. Если ссылка объекта указывает на объект, отличный от объекта из следующего списка, возникает ошибка:  
  
 База данных  
 Очищает кэш для всех измерений и секций, содержащихся в базе данных.  
  
 Измерение  
 Очищает кэш для указанного измерения.  
  
 Cube  
 Очищает кэш для всех секций, содержащихся в группе мер для куба.  
  
 Группа мер  
 Очищает кэш для всех секций, содержащихся в группе мер.  
  
 Partition (Раздел)  
 Очищает кэш для указанной секции.  
  
## <a name="see-also"></a>См. также:  
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  

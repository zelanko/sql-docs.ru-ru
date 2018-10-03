---
title: Управление кэшами (XMLA) | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 7e99be9f6a2af7dbbaab624ba592b2486cf807f2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48048164"
---
# <a name="managing-caches-xmla"></a>Управление кэшами (XMLA)
  Можно использовать [ClearCache](../xmla/xml-elements-commands/clearcache-element-xmla.md) в XML для аналитики (XMLA) для очистки кэша указанного измерения или секции. Очистка кэша вынуждает [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] перестроить кэш для этого объекта.  
  
## <a name="specifying-objects"></a>Указание объектов  
 [Объект](../xmla/xml-elements-properties/object-element-xmla.md) свойство `ClearCache` команда может содержать ссылку на объект только для одного из следующих объектов. Если ссылка объекта указывает на объект, отличный от объекта из следующего списка, возникает ошибка:  
  
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
  
## <a name="see-also"></a>См. также  
 [Разработка с использованием XMLA в службах Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  

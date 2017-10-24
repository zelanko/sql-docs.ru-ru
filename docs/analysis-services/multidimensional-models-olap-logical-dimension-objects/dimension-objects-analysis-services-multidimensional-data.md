---
title: "Измерение объектов (службы Analysis Services — многомерные данные) | Документы Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], objects
ms.assetid: 7f3d55c7-cccb-4ad0-b6cb-3a2c9992dd68
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 68fa5e37c0cc3620417f916ff35dcd6e3402d615
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="dimension-objects-analysis-services---multidimensional-data"></a>Объекты измерений (службы Analysis Services — многомерные данные)
  Простой объект <xref:Microsoft.AnalysisServices.Dimension> состоит из основной информации, атрибутов и иерархий. Основная информация включает имя измерения, тип измерения, источник данных, режим хранения и др. Атрибуты определяют фактические данные в измерении. Атрибуты не обязательно принадлежат к иерархии, но иерархии формируются из атрибутов. В иерархии создаются упорядоченные списки уровней и определяются способы, с помощью которых пользователь может исследовать данное измерение.  
  
## <a name="in-this-section"></a>В этом разделе  
 В следующих разделах приведена дополнительная информация о проектировании и реализации объектов измерения.  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Измерения (службы Analysis Services — многомерные данные)](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], измерения являются основными компонентами куба. В измерениях данные привязаны к некоторой предметной области, например заказчики, магазины или служащие.|  
|[Атрибуты и иерархии атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attributes-and-attribute-hierarchies.md)|Измерения — это коллекции атрибутов, которые в представлении источника данных привязаны к одному или нескольким столбцам таблицы или представления.|  
|[Связи атрибутов](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)|В [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], атрибуты измерения всегда связаны прямо или косвенно с ключевым атрибутом. Когда измерение определяется по схеме «звезда», где все атрибуты измерения наследуются из одной реляционной таблицы, то связи между ключевыми и не ключевыми атрибутами определяются автоматически. Когда измерение определяется по схеме «снежинка», где атрибуты измерения наследуются от разных реляционных таблиц, связи атрибутов автоматически определяются следующим образом:<br /><br /> Между ключевым атрибутом и каждым не ключевым атрибутом, привязанным к столбцу главной таблицы измерения.<br /><br /> Между ключевым атрибутом и атрибутами, привязанными к внешнему ключу вспомогательной таблицы, которая связывает таблицы базового измерения.<br /><br /> Между атрибутом, привязанным к внешнему ключу вспомогательной таблицы, и каждым не ключевым атрибутом, привязанным к столбцам вспомогательной таблицы.|  
  
  


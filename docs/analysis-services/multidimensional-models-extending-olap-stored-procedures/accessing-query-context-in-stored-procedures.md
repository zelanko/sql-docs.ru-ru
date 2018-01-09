---
title: "Доступ к контексту запросов в хранимых процедурах | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
caps.latest.revision: "22"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5b7a0c3e57a5249a26bf13a2cf9709e58df85da8
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2018
---
# <a name="accessing-query-context-in-stored-procedures"></a>Доступ к контексту запросов в хранимых процедурах
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Контекст выполнения хранимой процедуры доступен в рамках кода хранимой процедуры как **контекста** объект модели объектов сервера ADOMD.NET. Этот контекст доступен только для чтения и не может быть изменен хранимой процедурой. На этом объекте доступны следующие свойства.  
  
|Свойство|Тип|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Куб для текущего контекста запросов.|  
|**CurrentDatabaseName**|String|Идентификатор текущей базы данных.|  
|**CurrentConnection**|Соединение|Ссылка на объект подключения в текущем контексте.|  
|**Передать**|Целочисленный|Номера прохода для текущего контекста.|  
  
 **Контекста** существует, когда модель объектов многомерных выражений (MDX) используется в хранимой процедуре. Он не доступен, когда модель объектов многомерных выражений используется на клиенте. **Контекста** объекта явно не передан или возвращаемых хранимой процедурой. Он доступен во время выполнения хранимой процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками многомерной модели](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

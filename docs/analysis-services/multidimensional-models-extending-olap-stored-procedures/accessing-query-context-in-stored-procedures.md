---
title: Доступ к контексту запросов в хранимых процедурах | Документы Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 13facbc44747bedc6f28e1ff4d3bda81b60004ad
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/10/2018
---
# <a name="accessing-query-context-in-stored-procedures"></a>Доступ к контексту запросов в хранимых процедурах
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Контекст выполнения хранимой процедуры доступен в рамках кода хранимой процедуры как **контекста** объект модели объектов сервера ADOMD.NET. Этот контекст доступен только для чтения и не может быть изменен хранимой процедурой. На этом объекте доступны следующие свойства.  
  
|property|Тип|Описание|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Куб для текущего контекста запросов.|  
|**CurrentDatabaseName**|Строковые значения|Идентификатор текущей базы данных.|  
|**CurrentConnection**|Соединение|Ссылка на объект подключения в текущем контексте.|  
|**Передать**|Целочисленный|Номера прохода для текущего контекста.|  
  
 **Контекста** существует, когда модель объектов многомерных выражений (MDX) используется в хранимой процедуре. Он не доступен, когда модель объектов многомерных выражений используется на клиенте. **Контекста** объекта явно не передан или возвращаемых хранимой процедурой. Он доступен во время выполнения хранимой процедуры.  
  
## <a name="see-also"></a>См. также  
 [Управление сборками многомерной модели](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

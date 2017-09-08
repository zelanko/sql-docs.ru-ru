---
title: "Доступ к контексту запросов в хранимых процедурах | Документы Microsoft"
ms.custom: 
ms.date: 03/06/2017
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
- execution context [Analysis Services]
- stored procedures [Analysis Services], query context
- Context object
- query context [Analysis Services]
ms.assetid: bdc7dad8-2f22-4265-aba4-a3a451527840
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3ea922bed66dbcb625614259346794c9ba7856e9
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="accessing-query-context-in-stored-procedures"></a>Доступ к контексту запросов в хранимых процедурах
  Контекст выполнения хранимой процедуры доступен в рамках кода хранимой процедуры как **контекста** объект модели объектов сервера ADOMD.NET. Этот контекст доступен только для чтения и не может быть изменен хранимой процедурой. На этом объекте доступны следующие свойства.  
  
|Свойство|Тип|Description|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|Куб для текущего контекста запросов.|  
|**CurrentDatabaseName**|Строковые значения|Идентификатор текущей базы данных.|  
|**CurrentConnection**|Соединение|Ссылка на объект подключения в текущем контексте.|  
|**Передать**|Целочисленный|Номера прохода для текущего контекста.|  
  
 **Контекста** существует, когда модель объектов многомерных выражений (MDX) используется в хранимой процедуре. Он не доступен, когда модель объектов многомерных выражений используется на клиенте. **Контекста** объекта явно не передан или возвращаемых хранимой процедурой. Он доступен во время выполнения хранимой процедуры.  
  
## <a name="see-also"></a>См. также:  
 [Управление сборками многомерной модели](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [Определение хранимых процедур](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  

---
title: "Метод compareTo (DateTimeOffset) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 8ecd77b1080f1a5c49059f65e857d56c8d582b1b
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="compareto-method-datetimeoffset"></a>Метод compareTo (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сравнивает этот **DateTimeOffset** объекта в другой **DateTimeOffset** объекта на основе времени по Гринвичу.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int compareTo(DateTimeOffset other)  
```  
  
#### <a name="parameters"></a>Параметры  
 Объект [DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md) значение, которое требуется сравнить с текущим экземпляром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В следующей таблице описывается значение, возвращаемое данным методом.  
  
|Возвращаемое значение|Description|  
|------------------|-----------------|  
|0|Оба **DateTimeOffset** объекты представляют тот же момент времени.|  
|Отрицательное число|Это **DateTimeOffset** объект представляет точку во времени, предшествующую *других*.|  
|Положительное число|Это **DateTimeOffset** объект представляет точку во времени, после *других*.|  
  
## <a name="remarks"></a>Замечания  
 Если два **DateTimeOffset** объекты имеют то же время по Гринвичу, то дополнительное упорядочение объектов по смещению.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  

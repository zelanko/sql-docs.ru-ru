---
title: Метод compareTo (DateTimeOffset) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: b8307787576f520f83ceeffe10c830cd06a16d69
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
  
|Возвращаемое значение|Описание|  
|------------------|-----------------|  
|0|Оба **DateTimeOffset** объекты представляют тот же момент времени.|  
|Отрицательное число|Это **DateTimeOffset** объект представляет точку во времени, предшествующую *других*.|  
|Положительное число|Это **DateTimeOffset** объект представляет точку во времени, после *других*.|  
  
## <a name="remarks"></a>Замечания  
 Если два **DateTimeOffset** объекты имеют то же время по Гринвичу, то дополнительное упорядочение объектов по смещению.  
  
## <a name="see-also"></a>См. также  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  

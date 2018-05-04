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
ms.topic: conceptual
ms.assetid: e4cf2ea4-0fe9-40ce-ba79-f2a2b616997e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4d30f5d823a7f060c9920e74a5a4e5bed55b2821
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
  

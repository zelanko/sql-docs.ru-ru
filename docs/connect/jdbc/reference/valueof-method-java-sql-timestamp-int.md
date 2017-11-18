---
title: "Метод valueOf (java.sql.Timestamp, int) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b5bd8228a590f165b9df5df8dcc76798dea81e43
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="valueof-method-javasqltimestamp-int"></a>Метод valueOf (java.sql.Timestamp, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает **DateTimeOffset** объект, представляющий точку во времени с определенным смещением относительно среднего времени по Гринвичу заданному значению java.sql.Timestamp и значение, определяющее смещение в минутах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, int minutesOffset)  
```  
  
#### <a name="parameters"></a>Параметры  
 *timestamp*  
  
 Значениеjava.sql.Timestamp.  
  
 *minutesOffset*  
  
 Смещение в минутах.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект DateTimeOffset, представляющий точку во времени, заданную объектом java.sql.Timestamp с указанным смещением минутах от времени GMT.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  


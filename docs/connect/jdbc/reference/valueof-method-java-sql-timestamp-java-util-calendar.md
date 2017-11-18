---
title: "Метод valueOf (java.sql.Timestamp, java.util.Calendar) | Документы Microsoft"
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
ms.assetid: 7320c383-0b06-446d-963b-7005e50324a2
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b77f9ce80c54980a8a55d23b90667e2c07672caa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="valueof-method-javasqltimestamp-javautilcalendar"></a>Метод valueOf (java.sql.Timestamp, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Создает **DateTimeOffset** объект, представляющий точку во времени с определенным смещением относительно среднего времени по Гринвичу заданному значению java.sql.Timestamp и значению java.util.Calendar, указывающему смещение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public static DateTimeOffset valueOf(java.sql.Timestamp timestamp, java.util.Calendar calendar)  
```  
  
#### <a name="parameters"></a>Параметры  
 *timestamp*  
  
 Значениеjava.sql.Timestamp.  
  
 *Календарь*  
  
 Значение смещения.  Компоненты даты и времени *календаря* устанавливается в соответствии с *timestamp* значение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает объект DateTimeOffset, представляющий точку во времени, заданную объектом java.sql.Timestamp в объект заданного java.util.Calendar часового пояса.  
  
## <a name="remarks"></a>Замечания  
 Этот метод также задает объект java.util.Calendar до точки во времени, заданную объектом java.sql.Timestamp.  
  
## <a name="see-also"></a>См. также:  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  


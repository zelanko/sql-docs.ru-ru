---
title: Метод valueOf (java.sql.Timestamp, int) | Документы Microsoft
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
ms.assetid: 114f55af-62ab-4c60-8724-0affbbbbbcdc
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 09207f2feedb2f1e10485045a248454a12ddf06c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>См. также  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  

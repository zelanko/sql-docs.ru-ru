---
title: Метод getMinutesOffset (DateTimeOffset) | Документы Microsoft
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
ms.assetid: 18ba844a-ea36-42de-87da-bbc222082efe
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8ffaf44dae71da5c5f370c25dab87e4d799707dd
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="getminutesoffset-method-datetimeoffset"></a>Метод getMinutesOffset (DateTimeOffset)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает смещение в минутах от среднего времени по Гринвичу этого объекта DateTimeOffset.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMinutesOffset()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Смещение в минутах.  
  
## <a name="remarks"></a>Замечания  
 Для объекта DateTimeOffset, представляющего 8 марта 2010 11:35:48 -0800, getMinutesOffset возвращает значение 480.  
  
## <a name="see-also"></a>См. также  
 [Класс DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-class.md)   
 [Элементы DateTimeOffset](../../../connect/jdbc/reference/datetimeoffset-members.md)  
  
  

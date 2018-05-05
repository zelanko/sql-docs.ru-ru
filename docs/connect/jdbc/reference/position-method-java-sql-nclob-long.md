---
title: Метод position (java.sql.NClob, long) | Документы Microsoft
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
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8bcac66bf3ca49b7837d3b552d708cea16422de1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="position-method-javasqlnclob-long"></a>Метод position (java.sql.NClob, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает позицию символа, с которой указанный **NClob** объекта *searchstr* появляется в этом **NClob** объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
long position(java.sql.NClob searchstr,  
              long start)  
```  
  
#### <a name="parameters"></a>Параметры  
 *searchstr*  
  
 NClob объект, который требуется найти.  
  
 *start*  
  
 Позиция, с которой начнется поиск; отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Позиция, в которой находится подстрока, либо значение -1, если она не найдена. Позиция отсчитывается от 1.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод позиция указывается методом в интерфейсе java.sql.NClob позиции.  
  
## <a name="see-also"></a>См. также  
 [Метод Position &#40;SQLServerNClob&#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  

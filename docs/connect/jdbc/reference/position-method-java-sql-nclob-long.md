---
title: "Метод position (java.sql.NClob, long) | Документы Microsoft"
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
ms.assetid: f2354278-d128-4cf4-a170-22c05fcb763b
caps.latest.revision: "13"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4a4007d3e734210f8a60a56884898dfb48c7a970
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
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
  
 *Запуск*  
  
 Позиция, с которой начнется поиск; отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Позиция, в которой находится подстрока, либо значение -1, если она не найдена. Позиция отсчитывается от 1.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод позиция указывается методом в интерфейсе java.sql.NClob позиции.  
  
## <a name="see-also"></a>См. также:  
 [Поместите метод &#40; SQLServerNClob &#41;](../../../connect/jdbc/reference/position-method-sqlservernclob.md)   
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  

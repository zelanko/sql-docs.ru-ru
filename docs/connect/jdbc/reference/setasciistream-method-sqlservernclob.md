---
title: Метод setAsciiStream (SQLServerNClob) | Документы Microsoft
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
ms.assetid: 617ece92-0fb1-4f95-b32d-29b5b56eb3fb
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 9f54f4faa8a58b7df3cc257ebfa8cbbafa9bc5d3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="setasciistream-method-sqlservernclob"></a>Метод setAsciiStream (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает поток, который используется для записи ASCII символов, которое необходимо **NCLOB** этим **java.sql.NClob** представляет, начиная с указанной позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.io.OutputStream setAsciiStream(long pos)  
```  
  
#### <a name="parameters"></a>Параметры  
 *POS*  
  
 Позиция, с которой начинается запись **NCLOB** объекта; отсчитывается от 1.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект OutputStream, представляющий поток, к которому символы в кодировке ASCII могут быть записаны.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод setAsciiStream указывается с помощью метода setAsciiStream в интерфейсе java.sql.NClob.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [Элементы SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [Класс SQLServerNClob](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  

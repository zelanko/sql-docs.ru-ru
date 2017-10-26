---
title: "Метод getTimestamp (int, java.util.Calendar) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerCallableStatement.getTimestamp (int, java.util.Calendar)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 161c559a-8651-44ba-a914-15eb6a612417
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e5287bb088f4eeff8823ac28b0ffd8067ac93004
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="gettimestamp-method-int-javautilcalendar"></a>Метод getTimestamp (int, java.util.Calendar)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение указанного параметра в виде объекта java.sql.Timestamp на языке программирования индекс параметра с помощью календаря объекта Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Timestamp getTimestamp(int index,  
                                       java.util.Calendar cal)  
```  
  
#### <a name="parameters"></a>Параметры  
 *Индекс*  
  
 **Int** , указывающее индекс параметра.  
  
 *Клиентская лицензия*  
  
 Объект календаря.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект отметки времени.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getTimestamp указывается с помощью метода getTimestamp в интерфейсе java.sql.CallableStatement.  
  
 Этот метод возвращает значения только из [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] **datetime** и **smalldatetime** столбцов.  
  
## <a name="see-also"></a>См. также:  
 [Метод getTimestamp &#40; SQLServerCallableStatement &#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlservercallablestatement.md)   
 [Члены SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [Класс SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  


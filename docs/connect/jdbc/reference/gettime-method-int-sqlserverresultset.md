---
title: "Метод getTime (int) (SQLServerResultSet) | Документы Microsoft"
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
- SQLServerResultSet.getTime (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e18c84f5-7171-4057-8c9e-fe1d43ae9c20
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5608722069507b813213fe4489da115b7f6f37b3
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="gettime-method-int-sqlserverresultset"></a>Метод getTime (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение индекса заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта в виде объекта java.sql.Time на языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Time getTime(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект времени.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getTime указывается с помощью getTime метода в интерфейсе java.sql.ResultSet.  
  
 Этот метод возвращает допустимое время часть [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] типа данных datetime или smalldatetime, с частью даты, установленной в опорную дату Java 1970/01/01.  
  
## <a name="see-also"></a>См. также:  
 [Метод getTime &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/gettime-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  


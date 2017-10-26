---
title: "Метод getNClob (int) (SQLServerResultSet) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 103082e3-de98-4dff-8dc7-eaa5c64b1597
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bdd7f0bf2c87427d338c9e45ef19f4c9729289b8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getnclob-method-int-sqlserverresultset"></a>Метод getNClob (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает значение заданного столбца в текущей строке [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объект как объект NClob языке программирования Java.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.NClob getNClob(int columnIndex)  
```  
  
#### <a name="parameters"></a>Параметры  
 *columnIndex*  
  
 **Int** , указывающее индекс столбца.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект NClob.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getNClob указывается с помощью метода getNClob в интерфейсе java.sql.ResultSet.  
  
 Этот метод поддерживается только в **nvarchar(max)**, **ntext**, и **xml** столбцов. Использование этого метода при работе со столбцами других типов данных приведет к возникновению исключения.  
  
## <a name="see-also"></a>См. также:  
 [Метод getNClob &#40; SQLServerResultSet &#41;](../../../connect/jdbc/reference/getnclob-method-sqlserverresultset.md)   
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  


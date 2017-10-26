---
title: "Метод Next (SQLServerResultSet) | Документы Microsoft"
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
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5fe62919bd765d83e2d3a38a9cdda33d88312e29
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="next-method-sqlserverresultset"></a>Метод Next (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Перемещает курсор на одну строку вниз от текущей позиции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если допустимо новой текущей строкой. **false** Если больше нет строк для обработки.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот следующий метод указывается с помощью следующего метода в интерфейсе java.sql.ResultSet.  
  
 Курсор результирующего набора сначала располагается перед первой строкой. Первый вызов метода next выполняет первую строку текущей строки, второй вызов делает вторую строку текущей и т. д.  
  
 Если для текущей строки открыт входной поток, вызов метода next неявно закройте его. Цепочка предупреждений для [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта очищается, когда считывается новая строка.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  


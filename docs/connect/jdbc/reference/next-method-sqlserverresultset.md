---
title: Метод Next (SQLServerResultSet) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fa878b809af8dab927877f8af0db3d54a6a3eb30
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32840829"
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
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

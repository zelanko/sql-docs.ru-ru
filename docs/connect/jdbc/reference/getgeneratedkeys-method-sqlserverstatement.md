---
title: "Метод getGeneratedKeys (SQLServerStatement) | Документы Microsoft"
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
- SQLServerStatement.getGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3325950-0e81-4ae8-aa0c-e1f6d371adcd
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 224930c0a364158033e0e30ccfe855f8b71579aa
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getgeneratedkeys-method-sqlserverstatement"></a>Метод getGeneratedKeys (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает все автоматически сформированные ключи, созданные в результате при выполнении этого [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.ResultSet getGeneratedKeys()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект результирующего набора.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getGeneratedKeys указывается с помощью метода getGeneratedKeys в интерфейсе java.sql.Statement.  
  
 Дополнительные сведения об использовании этого метода см. в разделе [с помощью автоматически сформированных ключей](../../../connect/jdbc/using-auto-generated-keys.md).  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  


---
title: "Метод supportsSubqueriesInExists (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.supportsSubqueriesInExists
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 14c08c7f-5c1e-4e21-8373-ae32c22e47d4
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 72e229a1b1c1657ada63ec680201441f5014dd0c
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="supportssubqueriesinexists-method-sqlserverdatabasemetadata"></a>Метод supportsSubqueriesInExists (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных вложенные запросы в выражениях EXISTS.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsSubqueriesInExists()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод supportsSubqueriesInExists указывается с помощью метода supportsSubqueriesInExists в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

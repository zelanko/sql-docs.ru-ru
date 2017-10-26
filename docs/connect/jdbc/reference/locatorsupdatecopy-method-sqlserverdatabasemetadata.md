---
title: "Метод locatorsUpdateCopy (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.locatorsUpdateCopy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6ec8c1d-7ff8-4bc5-8bd3-0199a9294a6e
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 6feace96a0a6d2aeeb305b1a2732ab66a68ef281
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="locatorsupdatecopy-method-sqlserverdatabasemetadata"></a>Метод locatorsUpdateCopy (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, будут ли обновления в LOB производиться над этим объектом LOB напрямую, либо над его копией.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean locatorsUpdateCopy()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если обновления выполняются в копии. **false** Если обновления выполняются непосредственно.  
  
## <a name="exceptions"></a>Исключения  
 java.sql.SQLException  
  
## <a name="remarks"></a>Замечания  
 Этот метод locatorsUpdateCopy указывается с помощью метода locatorsUpdateCopy в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


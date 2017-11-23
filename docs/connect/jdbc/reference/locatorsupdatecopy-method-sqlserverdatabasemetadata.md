---
title: "Метод locatorsUpdateCopy (SQLServerDatabaseMetaData) | Документы Microsoft"
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
apiname: SQLServerDatabaseMetaData.locatorsUpdateCopy
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: f6ec8c1d-7ff8-4bc5-8bd3-0199a9294a6e
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7097d5586b233547574fc3fbe3c982586e90962c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
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
  
  

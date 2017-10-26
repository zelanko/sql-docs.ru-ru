---
title: "Метод supportsOpenCursorsAcrossCommit | Документы Microsoft"
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
- SQLServerDatabaseMetaData.supportsOpenCursorsAcrossCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b7eed108-64cc-4be6-b297-8af6c1e3dc72
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 4fedc2b8e9eed5fc2083d0258c4191934f7a81db
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="supportsopencursorsacrosscommit-method-sqlserverdatabasemetadata"></a>Метод supportsOpenCursorsAcrossCommit (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных сохранение курсоров открытыми между фиксациями транзакций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsOpenCursorsAcrossCommit()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод supportsOpenCursorsAcrossCommit указывается с помощью метода supportsOpenCursorsAcrossCommit в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


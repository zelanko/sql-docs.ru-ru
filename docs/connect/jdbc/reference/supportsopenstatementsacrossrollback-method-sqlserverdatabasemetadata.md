---
title: "Метод supportsOpenStatementsAcrossRollback | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.supportsOpenStatementsAcrossRollback
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4e38b938-f39f-4c5d-9b32-4ba489535c45
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ac0ae345a7e305ad3dfcb5558b78e48c3cad8717
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="supportsopenstatementsacrossrollback-method-sqlserverdatabasemetadata"></a>Метод supportsOpenStatementsAcrossRollback (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных сохранение инструкций открытыми между откатами транзакций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsOpenStatementsAcrossRollback()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод supportsOpenStatementsAcrossRollback указывается с помощью метода supportsOpenStatementsAcrossRollback в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


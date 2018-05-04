---
title: Метод supportsOpenCursorsAcrossRollback | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsOpenCursorsAcrossRollback
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4bc3e82b-a7e7-43a5-8938-6f29c7570163
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fc21da7af6a3d0a2dbfed43a8de89a91f8407b28
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="supportsopencursorsacrossrollback-method-sqlserverdatabasemetadata"></a>Метод supportsOpenCursorsAcrossRollback (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных сохранение курсоров открытыми между откатами транзакций.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsOpenCursorsAcrossRollback()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод supportsOpenCursorsAcrossRollback указывается с помощью метода supportsOpenCursorsAcrossRollback в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

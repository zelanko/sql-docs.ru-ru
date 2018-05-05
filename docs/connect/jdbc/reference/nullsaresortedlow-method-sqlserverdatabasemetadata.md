---
title: Метод nullsAreSortedLow (SQLServerDatabaseMetaData) | Документы Microsoft
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
- SQLServerDatabaseMetaData.nullsAreSortedLow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 30c06a9d-3513-42d0-8b2a-5a20ac31eb0e
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 559f83d9585f13c4789a4857a511eb644e788244
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="nullsaresortedlow-method-sqlserverdatabasemetadata"></a>Метод nullsAreSortedLow (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, считаются ли значения NULL маленькими при сортировке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean nullsAreSortedLow()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если значения считаются маленькими при сортировке. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод nullsAreSortedLow указывается с помощью метода nullsAreSortedLow в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

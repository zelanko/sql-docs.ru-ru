---
title: Метод supportsMultipleResultSets (SQLServerDatabaseMetaData) | Документы Microsoft
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
- SQLServerDatabaseMetaData.supportsMultipleResultSets
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cb4d0b91-db1d-4a6f-a87c-8ea125215afc
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dc1d04f8dacfd5ec6276737065639fc4dbea7bf
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="supportsmultipleresultsets-method-sqlserverdatabasemetadata"></a>Метод supportsMultipleResultSets (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сообщает, является ли эта база данных поддерживает несколько [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объектов из одного вызова [выполнение](../../../connect/jdbc/reference/execute-method.md) метод [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsMultipleResultSets()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод supportsMultipleResultSets указывается с помощью метода supportsMultipleResultSets в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

---
title: "Метод executeBatch (SQLServerPreparedStatement) | Документы Microsoft"
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
apiname: SQLServerPreparedStatement.executeBatch
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 8418167e-cbd2-464d-b118-73cdd76080ed
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a459eef327f162e362cf5f86fbba1c2a726e78af
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="executebatch-method-sqlserverpreparedstatement"></a>Метод executeBatch (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Отправляет пакет команд базе данных для выполнения. В случае успешного выполнения всех команд возвращает массив из количества операций обновления, выполненных той или иной командой.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Массив значений типа int, содержащий счетчики обновлений.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>Замечания  
 Этот метод executeBatch указывается с помощью метода executeBatch в интерфейсе java.sql.Statement.  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Версии 3.0 драйвера JDBC совместим с JDBC 4.0, согласно, вызов метода CallableStatement.executeBatch (наследуется от PreparedStatement) вызовет BatchUpdateException, если хранимая процедура принимает OUT или INOUT параметры или возвращает что-нибудь кроме счетчика обновления.  
  
 Этот метод переопределяет [SQLServerStatement.executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

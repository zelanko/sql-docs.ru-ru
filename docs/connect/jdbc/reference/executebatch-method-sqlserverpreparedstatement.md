---
title: Метод executeBatch (SQLServerPreparedStatement) | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8418167e-cbd2-464d-b118-73cdd76080ed
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 91ed9bb1623b6427b0fc2f462702ca28e8dd5062
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
    
 Этот метод переопределяет [SQLServerStatement.executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>См. также  
 [Члены SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

---
description: Метод execute (java.lang.String)
title: Метод execute (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a871917e-d286-46c3-96cf-2e8e8b22111c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0375eb9dd2d9252ed914fa554beb54faa7e345ef
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437756"
---
# <a name="execute-method-javalangstring"></a>Метод execute (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL, которая может возвращать несколько результатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение типа **String**, содержащее инструкцию SQL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если инструкция возвращает результирующий набор. **false**, если инструкция возвращает число обновлений или не возвращает результата.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод execute определен с помощью метода execute в интерфейсе java.sql.Statement.  
  
 Этот метод переопределяет метод [execute](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md), содержащийся в классе [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 Вызов этого метода приводит к исключению, поскольку инструкция SQL для объекта SQLServerPreparedStatement определена при создании объекта.  
  
## <a name="see-also"></a>См. также:  
 [Метод execute (SQLServerPreparedStatement)](../../../connect/jdbc/reference/execute-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

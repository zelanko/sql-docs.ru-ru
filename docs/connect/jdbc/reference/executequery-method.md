---
title: Метод executeQuery () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1d90407f-16df-4ba2-b4a5-47d5751e1d7c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1f80cceb8807fc643e197d06ae737ee7347e1be1
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954760"
---
# <a name="executequery-method-"></a>Метод executeQuery ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет SQL-запрос в этом объекте [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и возвращает объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md), созданный запросом.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet executeQuery()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SQLServerResultSet.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод executeQuery определен с помощью метода executeQuery в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод executeQuery (SQLServerPreparedStatement)](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

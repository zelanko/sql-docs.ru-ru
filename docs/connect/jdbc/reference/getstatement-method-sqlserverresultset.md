---
description: Метод getStatement (SQLServerResultSet)
title: Метод getStatement (SQLServerResultSet) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getStatement
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7dea981b-b4fd-4f8d-954f-e686124627e2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f5affe4faf9a3c4f732d13d4c5ac54b442a28c83
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434396"
---
# <a name="getstatement-method-sqlserverresultset"></a>Метод getStatement (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает объект [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), на основе которого был создан этот объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.Statement getStatement()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SQLServerStatement.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getStatement задается с помощью метода getStatement в интерфейсе java.sql.ResultSet.  
  
 Если результирующий набор был получен другим образом, например методом [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), то этот метод возвращает значение NULL.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [Класс SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  

---
description: Метод executeQuery (java.lang.String)
title: Метод executeQuery (java.lang.String) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeQuery (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 610205c2-6bcd-426c-ad6f-9682551efdec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: cff547cf27a6ef796e31383e524872717943b860
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437706"
---
# <a name="executequery-method-javalangstring"></a>Метод executeQuery (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL и возвращает один объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final java.sql.ResultSet executeQuery(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение типа **String**, содержащее инструкцию SQL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект SQLServerResultSet.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод executeQuery определен с помощью метода executeQuery в интерфейсе java.sql.Statement.  
  
 Этот метод переопределяет метод [executeQuery](../../../connect/jdbc/reference/executequery-method-sqlserverstatement.md), содержащийся в классе [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
 Вызов этого метода приводит к исключению, поскольку инструкция SQL для объекта SQLServerPreparedStatement определена при создании объекта.  
  
 Исключение [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md) вызывается, если заданная инструкция SQL дает любой результат, кроме одиночного объекта [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="see-also"></a>См. также:  
 [Метод executeQuery (SQLServerPreparedStatement)](../../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

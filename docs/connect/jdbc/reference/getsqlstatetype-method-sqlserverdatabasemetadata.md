---
title: Метод getSQLStateType (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSQLStateType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ee4d6751-68a3-4d04-831c-e6d704c59e63
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 76faa3bcaccac4f75d95dc49276c669a5631b5a8
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67979734"
---
# <a name="getsqlstatetype-method-sqlserverdatabasemetadata"></a>Метод getSQLStateType (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Указывает, равно ли состояние SQLSTATE, возвращенное методом SQLException.getSQLState, X/Open (теперь называется Open Group), SQL CLI, SQL99 (JDBC 3.0) или SQL:2003 (JDBC 4.0).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getSQLStateType()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, указывающее тип SQLSTATE. Может принимать одно из следующих значений.  
  
-   Для среды выполнения Java версии 5.0. Если свойство подключения **xopenStates** имеет значение **true**, этот метод возвращает DatabaseMetaData.sqlStateXOpen. В противном случае — DatabaseMetaData.sqlStateSQL99.  
  
-   Для среды выполнения Java версии 6.0. Если свойство подключения **xopenStates** имеет значение **true**, этот метод возвращает DatabaseMetaData.sqlStateXOpen. В противном случае — DatabaseMetaData.sqlStateSQL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getSQLStateType определен с помощью метода getSQLStateType в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

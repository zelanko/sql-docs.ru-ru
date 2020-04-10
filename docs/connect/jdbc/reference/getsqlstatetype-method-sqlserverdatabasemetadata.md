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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 762c22bbf2ed499fc2c0884014e374af17f60292
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921951"
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
  
  

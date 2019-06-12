---
title: Метод supportsMultipleResultSets (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsMultipleResultSets
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cb4d0b91-db1d-4a6f-a87c-8ea125215afc
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c6abf07e5ff18fba6fd68e8c109388f82bc5eae4
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764137"
---
# <a name="supportsmultipleresultsets-method-sqlserverdatabasemetadata"></a>Метод supportsMultipleResultSets (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает значение, определяющее, поддерживает ли эта база данных получение нескольких объектов [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) в единственном вызове метода [execute](../../../connect/jdbc/reference/execute-method.md) класса [SQLServerCallableStatement](../../../connect/jdbc/reference/sqlservercallablestatement-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsMultipleResultSets()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsMultipleResultSets указывается с помощью метода supportsMultipleResultSets в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

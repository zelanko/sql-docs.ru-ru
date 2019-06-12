---
title: Метод allTablesAreSelectable (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.allTablesAreSelectable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb340450-45a7-49c8-84bc-1b9dd5ee842f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fbc609140cf15e90e409cf123f59ae3409d15a26
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803693"
---
# <a name="alltablesareselectable-method-sqlserverdatabasemetadata"></a>Метод allTablesAreSelectable (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, имеет ли текущий пользователь разрешения на использование любых таблиц, возвращаемых методом [getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) в инструкции SELECT.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean allTablesAreSelectable()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если пользователь имеет разрешения на использование всех таблиц. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод allTablesAreSelectable указывается с помощью метода allTablesAreSelectable в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

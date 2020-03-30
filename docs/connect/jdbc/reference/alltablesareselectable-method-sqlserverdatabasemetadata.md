---
title: Метод allTablesAreSelectable (SQLServerDatabaseMetaData) | Документация Майкрософт
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
ms.openlocfilehash: f2fa61d7239858cb3479e7eeaa730e4197bf6bc5
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955863"
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
 Этот метод allTablesAreSelectable задается с помощью метода allTablesAreSelectable в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

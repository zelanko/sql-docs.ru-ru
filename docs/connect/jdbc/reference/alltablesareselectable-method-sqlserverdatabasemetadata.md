---
title: Метод allTablesAreSelectable (SQLServerDatabaseMetaData) | Документы Microsoft
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
- SQLServerDatabaseMetaData.allTablesAreSelectable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eb340450-45a7-49c8-84bc-1b9dd5ee842f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5b3f5139529d773f0b8559cfb6af203031cc6d36
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
ms.locfileid: "32828099"
---
# <a name="alltablesareselectable-method-sqlserverdatabasemetadata"></a>Метод allTablesAreSelectable (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Сообщает, является ли текущий пользователь имеет разрешения на использование всех таблиц, возвращаемых [getTables](../../../connect/jdbc/reference/gettables-method-sqlserverdatabasemetadata.md) метод в инструкции SELECT.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean allTablesAreSelectable()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если пользователь имеет разрешения на вызов использование всех таблиц. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод allTablesAreSelectable указывается с помощью метода allTablesAreSelectable в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

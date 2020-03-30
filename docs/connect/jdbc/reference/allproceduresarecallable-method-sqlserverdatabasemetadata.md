---
title: Метод allProceduresAreCallable (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.allProceduresAreCallable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8886137d-455e-497c-afea-4b326eda52f1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 559c025a5fcb7d27f4520cea0868761b449107a9
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955926"
---
# <a name="allproceduresarecallable-method-sqlserverdatabasemetadata"></a>Метод allProceduresAreCallable (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, имеет ли текущий пользователь разрешения на вызов любых процедур, возвращаемых методом [getProcedures](../../../connect/jdbc/reference/getprocedures-method-sqlserverdatabasemetadata.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean allProceduresAreCallable()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если пользователь имеет разрешения на вызов всех процедур. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод allProceduresAreCallable задается с помощью метода allProceduresAreCallable в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

---
title: Метод executeUpdate () | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeUpdate ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ca534c6b-ef4d-4ae8-8cc3-514728623cff
author: MightyPen
ms.author: genemi
ms.openlocfilehash: eae73888b97b8511a23ba3387e2674bff40643c2
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954585"
---
# <a name="executeupdate-method-"></a>Метод executeUpdate ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет в этом объекте [SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) инструкцию SQL. Это должна быть инструкция SQL INSERT, UPDATE, MERGE или DELETE, либо инструкция SQL, не возвращающая значения, например инструкция DDL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int executeUpdate()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, указывающее либо число обработанных строк, либо значение 0 для инструкций языка DDL.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод executeUpdate определен с помощью метода executeUpdate в интерфейсе java.sql.PreparedStatement.  
  
## <a name="see-also"></a>См. также:  
 [Метод executeUpdate (SQLServerPreparedStatement)](../../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md)   
 [Элементы SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Класс SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  

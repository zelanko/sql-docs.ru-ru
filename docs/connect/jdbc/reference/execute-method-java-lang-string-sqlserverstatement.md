---
title: Метод execute (java.lang.String) (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.execute (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 64ac78b8-d5b3-4134-9b72-d2b0c52168a2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 98adf628c3cc84442d34d6f1f07431a3c5918a31
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80922089"
---
# <a name="execute-method-javalangstring-sqlserverstatement"></a>Метод execute (java.lang.String) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL, которая может возвращать несколько результатов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean execute(java.lang.String sql)  
```  
  
#### <a name="parameters"></a>Параметры  
 *sql*  
  
 Значение типа **String**, содержащее инструкцию SQL.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если первый результат является результирующим набором. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод execute определен с помощью метода execute в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Метод execute (SQLServerStatement)](../../../connect/jdbc/reference/execute-method-sqlserverstatement.md)   
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

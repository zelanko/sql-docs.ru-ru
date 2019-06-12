---
title: Метод getUpdateCount (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6f05796220e305a0d6e06e15a58f780048d49a53
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790526"
---
# <a name="getupdatecount-method-sqlserverstatement"></a>Метод getUpdateCount (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает текущий результат в виде счетчика обновлений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, содержащее счетчик обновлений. Если возвращенный результат представляет объект результирующего набора или присутствует несколько результатов, то возвращается значение -1.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getUpdateCount указывается с помощью метода getUpdateCount в интерфейсе java.sql.Statement.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

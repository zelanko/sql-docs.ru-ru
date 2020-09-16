---
description: Метод getTransactionIsolation (SQLServerConnection)
title: Метод getTransactionIsolation (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 179772e9-6572-4ce5-83c5-ab2b196cee67
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 53d49dd19d57d8e7c520601711165d09bbe6c6e3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434026"
---
# <a name="gettransactionisolation-method-sqlserverconnection"></a>Метод getTransactionIsolation (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает текущий уровень изоляции транзакции для данного объекта [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getTransactionIsolation()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, содержащее один из следующих уровней изоляции.  
  
 TRANSACTION_NONE  
  
 TRANSACTION_READ_UNCOMMITTED  
  
 TRANSACTION_READ_COMMITTED  
  
 TRANSACTION_REPEATABLE_READ  
  
 TRANSACTION_SERIALIZABLE  
  
 TRANSACTION_SNAPSHOT = 0x1000  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getTransactionIsolation задается с помощью метода getTransactionIsolation в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

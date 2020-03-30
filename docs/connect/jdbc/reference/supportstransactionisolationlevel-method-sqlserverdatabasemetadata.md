---
title: Метод supportsTransactionIsolationLevel | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsTransactionIsolationLevel
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b716ed6c-6ec3-47a7-8e6d-16cbf2469d6d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ecfbc637db90531378d589043b637596c4ec2ee3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67968668"
---
# <a name="supportstransactionisolationlevel-method-sqlserverdatabasemetadata"></a>Метод supportsTransactionIsolationLevel (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных заданный уровень изоляции транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsTransactionIsolationLevel(int level)  
```  
  
#### <a name="parameters"></a>Параметры  
 *level*  
  
 Значение **int**, которое указывает уровень изоляции транзакций.  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsTransactionIsolationLevel задается с помощью метода supportsTransactionIsolationLevel в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

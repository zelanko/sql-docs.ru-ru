---
title: Метод getDefaultTransactionIsolation (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getDefaultTransactionIsolation
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 85b867ed-de5a-4879-b3f8-bce897879077
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e2349dbe193834385869f86f87fe4284a967284
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67983688"
---
# <a name="getdefaulttransactionisolation-method-sqlserverdatabasemetadata"></a>Метод getDefaultTransactionIsolation (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает уровень изоляции транзакций по умолчанию для этой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getDefaultTransactionIsolation()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа **int**, которое указывает уровень изоляции транзакций по умолчанию.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getDefaultTransactionIsolation задается с помощью метода getDefaultTransactionIsolation в интерфейсе java.sql.DatabaseMetaData.  
  
 При использовании [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с базой данных [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] этот метод возвращает значение TRANSACTION_READ_COMMITTED либо значение типа **int**, равное 2.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

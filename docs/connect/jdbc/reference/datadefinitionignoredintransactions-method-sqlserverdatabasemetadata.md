---
title: Игнорирование инструкции определения данных в транзакции | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.dataDefinitionIgnoredInTransactions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1674fb46-43a7-46d0-9f05-cf993d3bc032
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4d1538cc4aaf3e62086f57602b29ce0e61bceb6a
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "67955209"
---
# <a name="datadefinitionignoredintransactions-method-sqlserverdatabasemetadata"></a>Метод dataDefinitionIgnoredInTransactions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, учитывает ли эта база данных инструкции определения данных в пределах транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean dataDefinitionIgnoredInTransactions()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если инструкции DDL в транзакциях не обрабатываются. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод dataDefinitionIgnoredInTransactions определен с помощью метода dataDefinitionIgnoredInTransactions в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

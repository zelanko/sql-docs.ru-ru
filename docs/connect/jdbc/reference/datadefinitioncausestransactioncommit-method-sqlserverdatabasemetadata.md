---
title: Фиксации транзакции Force инструкции определения данных. | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.dataDefinitionCausesTransactionCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf04fa73-b9f1-4403-b6a0-e53d0d27c671
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9c22e224e7d95104593987f21dd2801d93ea78e6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="datadefinitioncausestransactioncommit-method-sqlserverdatabasemetadata"></a>Метод dataDefinitionCausesTransactionCommit (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, приводит ли выполнение инструкции определения базы данных в транзакции к фиксации транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean dataDefinitionCausesTransactionCommit()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** Если инструкция DDL вызывает принудительную фиксацию. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод dataDefinitionCausesTransactionCommit указывается с помощью метода dataDefinitionCausesTransactionCommit в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

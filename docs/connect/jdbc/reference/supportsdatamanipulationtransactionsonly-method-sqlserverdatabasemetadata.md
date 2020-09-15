---
description: Метод supportsDataManipulationTransactionsOnly (SQLServerDatabaseMetaData)
title: Метод supportsDataManipulationTransactionsOnly | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsDataManipulationTransactionsOnly
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bdc182db-4518-4bf2-b63a-05f58fdb4eb8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3c15e061c543b066adc773366756baae8fbb3d2c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88354120"
---
# <a name="supportsdatamanipulationtransactionsonly-method-sqlserverdatabasemetadata"></a>Метод supportsDataManipulationTransactionsOnly (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных только инструкции обработки данных в транзакции.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsDataManipulationTransactionsOnly()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsDataManipulationTransactionsOnly задается с помощью метода supportsDataManipulationTransactionsOnly в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

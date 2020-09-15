---
description: Метод supportsResultSetHoldability (SQLServerDatabaseMetaData)
title: Метод supportsResultSetHoldability (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsResultSetHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ab575792-fd11-4ff3-8847-1368e7a322c5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d0ed1388fd8e3d137fbaae9d7bc8b66235a8a5fe
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88354000"
---
# <a name="supportsresultsetholdability-method-sqlserverdatabasemetadata"></a>Метод supportsResultSetHoldability (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных заданную возможность сохранения результирующих наборов.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsResultSetHoldability(int holdability)  
```  
  
#### <a name="parameters"></a>Параметры  
 *holdability*  
  
 Значение **int**, указывающее возможность ожидания результирующего набора. Возможны следующие значения:  
  
 ResultSet.HOLD_CURSORS_OVER_COMMIT  
  
 ResultSet.CLOSE_CURSORS_AT_COMMIT  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsResultSetHoldability указывается с помощью метода supportsResultSetHoldability в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

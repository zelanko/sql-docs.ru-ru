---
description: Метод nullsAreSortedLow (SQLServerDatabaseMetaData)
title: Метод nullsAreSortedLow (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.nullsAreSortedLow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 30c06a9d-3513-42d0-8b2a-5a20ac31eb0e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 33239e2f4755adb526b9b81158efd2498702452f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433136"
---
# <a name="nullsaresortedlow-method-sqlserverdatabasemetadata"></a>Метод nullsAreSortedLow (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, считаются ли значения NULL маленькими при сортировке.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean nullsAreSortedLow()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **true**, если значения сортируются по уменьшению. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод nullsAreSortedLow задается с помощью метода nullsAreSortedLow в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

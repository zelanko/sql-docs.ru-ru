---
description: Метод supportsUnionAll (SQLServerDatabaseMetaData)
title: Метод supportsUnionAll (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsUnionAll
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ed8344eb-4d1d-43d3-ade8-935ec677f73c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2dff8fe5a894ff7bb92013576140888f32b99842
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431446"
---
# <a name="supportsunionall-method-sqlserverdatabasemetadata"></a>Метод supportsUnionAll (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает значение, определяющее, поддерживает ли эта база данных SQL UNION ALL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean supportsUnionAll()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **true**, если поддерживается. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод supportsUnionAll задается с помощью метода supportsUnionAll в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

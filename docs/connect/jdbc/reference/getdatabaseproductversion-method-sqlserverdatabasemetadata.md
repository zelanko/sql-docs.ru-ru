---
description: Метод getDatabaseProductVersion (SQLServerDatabaseMetaData)
title: Метод getDatabaseProductVersion (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getDatabaseProductVersion
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 19c0c15d-223f-45bd-a215-2867dfefecb0
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3d86ab32d0327ec6dadc830d3d76ea4e611d7a80
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436396"
---
# <a name="getdatabaseproductversion-method-sqlserverdatabasemetadata"></a>Метод getDatabaseProductVersion (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает номер версии данного продукта базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getDatabaseProductVersion()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее номер версии продукта базы данных.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getDatabaseProductVersion задается с помощью метода getDatabaseProductVersion в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

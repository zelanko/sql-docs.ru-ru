---
description: Метод getDatabaseMajorVersion (SQLServerDatabaseMetaData)
title: Метод getDatabaseMajorVersion (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getDatabaseMajorVersion
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 30860c07-e84b-428a-922a-ba63c070cd9c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a559047c604ced12168fcb7d2e4ee8fd9e9cc2f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436466"
---
# <a name="getdatabasemajorversion-method-sqlserverdatabasemetadata"></a>Метод getDatabaseMajorVersion (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает основной номер версии базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getDatabaseMajorVersion()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, которое указывает основной номер версии базы данных.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getDatabaseMajorVersion задается с помощью метода getDatabaseMajorVersion в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

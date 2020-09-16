---
description: Метод getJDBCMajorVersion (SQLServerDatabaseMetaData)
title: Метод getJDBCMajorVersion (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getJDBCMajorVersion
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 67b2bb4b-9714-4ba5-8739-50c632830451
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f90e4135f4fbef77c5d5c6fa22baefc445dab98e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435816"
---
# <a name="getjdbcmajorversion-method-sqlserverdatabasemetadata"></a>Метод getJDBCMajorVersion (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает основной номер версии JDBC для этого драйвера.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getJDBCMajorVersion()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **int**, которое указывает основной номер версии JDBC.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getConnection задается с помощью метода getConnection в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

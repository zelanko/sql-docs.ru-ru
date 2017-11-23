---
title: "Метод doesMaxRowSizeIncludeBlobs (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.doesMaxRowSizeIncludeBlobs
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 0c90a7a7-5a59-4858-bb26-3e725d8611d7
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 30f0afda970fb27c762c57d9ba3c81387829c0b2
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="doesmaxrowsizeincludeblobs-method-sqlserverdatabasemetadata"></a>Метод doesMaxRowSizeIncludeBlobs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает ли возвращаемое значение для [getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md) метод включает типы данных SQL LONGVARCHAR и LONGVARBINARY.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public boolean doesMaxRowSizeIncludeBlobs()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **значение true,** , если возвращаемое значение включает типы данных. В противном случае — **false**.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод doesMoxRowSizeIncludeBlobs указывается с помощью метода doesMoxRowSizeIncludeBlobs в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

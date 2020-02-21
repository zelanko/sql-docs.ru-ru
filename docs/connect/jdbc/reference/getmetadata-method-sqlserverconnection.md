---
title: Метод getMetaData (SQLServerConnection) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getMetaData
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 86223cb5-3bf4-489a-8c82-669a91764f2b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 4fdf49c68acd2ef1b1544ad02efcb4079ceeac67
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "67981852"
---
# <a name="getmetadata-method-sqlserverconnection"></a>Метод getMetaData (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает объект [SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md), который содержит метаданные базы данных, подключение к которой представляет данный объект [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.DatabaseMetaData getMetaData()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект DatabaseMetaData.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMetaData задается с помощью метода getMetaData в интерфейсе java.sql.Connection.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [Класс SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  

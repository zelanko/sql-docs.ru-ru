---
title: Метод getMaxCatalogNameLength (SQLServerDatabaseMetaData) | Документы Microsoft
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
- SQLServerDatabaseMetaData.getMaxCatalogNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 89c11327-eae1-4178-9e26-4b484d521c65
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 76987da1dc4fa130e07fafe5e61dc5d5c1bb6f6f
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="getmaxcatalognamelength-method-sqlserverdatabasemetadata"></a>Метод getMaxCatalogNameLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимальное число символов, допустимое в имени каталога для этой базы данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMaxCatalogNameLength()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 **Int** , указывающее максимально допустимое число символов.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getMaxCatalogNameLength указывается с помощью метода getMaxCatalogNameLength в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

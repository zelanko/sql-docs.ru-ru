---
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
ms.openlocfilehash: 486b064aaac56599379aa1a52fa24ff075d771ae
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923232"
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
  
  

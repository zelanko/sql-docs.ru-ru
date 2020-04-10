---
title: Метод getDriverVersion (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getDriverVersion
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3be84d65-af61-4c34-b052-74a5d488eaa9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1066be205916f23747da8fdd61a3ebf0784742ad
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80902100"
---
# <a name="getdriverversion-method-sqlserverdatabasemetadata"></a>Метод getDriverVersion (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает номер версии данного драйвера JDBC.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getDriverVersion()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее версию драйвера JDBC.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getDriverVersion задается с помощью метода getDriverVersion в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

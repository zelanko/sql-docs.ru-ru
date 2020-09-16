---
description: Метод getSystemFunctions (SQLServerDatabaseMetaData)
title: Метод getSystemFunctions (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSystemFunctions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6d390ec5-9ee2-49c4-b661-a93b55691dd1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a15a0a39c9da932e132e6b765e1ea3daf7f6519e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434236"
---
# <a name="getsystemfunctions-method-sqlserverdatabasemetadata"></a>Метод getSystemFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает список с разделителями-запятыми системных функций, доступных в этой базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSystemFunctions()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение **String**, содержащее список системных функций.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getSystemFunctions определен с помощью метода getSystemFunctions в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

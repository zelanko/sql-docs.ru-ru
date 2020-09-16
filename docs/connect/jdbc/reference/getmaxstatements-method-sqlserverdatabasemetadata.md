---
description: Метод getMaxStatements (SQLServerDatabaseMetaData)
title: Метод getMaxStatements (SQLServerDatabaseMetaData) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxStatements
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 71d58431-b671-49c5-939a-f581d1fef7cd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 65b697414aadc3ded169cd70f19f8f923886c699
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435496"
---
# <a name="getmaxstatements-method-sqlserverdatabasemetadata"></a>Метод getMaxStatements (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Возвращает максимальное число активных инструкций для этой базы данных, которые могут быть открыты одновременно.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public int getMaxStatements()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение типа**int**, указывающее максимально допустимое количество активных инструкций.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 Этот метод getMaxStatements задается с помощью метода getMaxStatements в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

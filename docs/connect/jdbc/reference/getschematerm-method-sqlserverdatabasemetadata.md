---
title: "Метод getSchemaTerm (SQLServerDatabaseMetaData) | Документы Microsoft"
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
apiname: SQLServerDatabaseMetaData.getSchemaTerm
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 3e4a400f-0859-4ac3-983e-c25633b33683
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 50df53f6f7eae8c825a9420aaf24288081e413f5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="getschematerm-method-sqlserverdatabasemetadata"></a>Метод getSchemaTerm (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает предпочтительный термин для схемы в этой базе данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getSchemaTerm()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее предпочтительный термин.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSchemaTerm указывается с помощью метода getSchemaTerm в интерфейсе java.sql.DatabaseMetaData.  
  
 При использовании [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, этот метод возвращает «schema» предпочтительный термин.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

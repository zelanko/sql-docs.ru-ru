---
title: "Метод getIdentifierQuoteString (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getIdentifierQuoteString
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6dea35a0-56a8-412c-8cd3-6539527ff597
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ae48037425e4201124e92a02d7bd1e3107a6a73b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getidentifierquotestring-method-sqlserverdatabasemetadata"></a>Метод getIdentifierQuoteString (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает **строка** , используемый для заключения в кавычки идентификаторов SQL.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getIdentifierQuoteString()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащий идентификаторы в кавычках.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getIdentifierQuoteString указывается с помощью метода getIdentifierQuoteString в интерфейсе java.sql.DatabaseMetaData.  
  
 При использовании [!INCLUDE[msCoName](../../../includes/msconame_md.md)] драйвера JDBC с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, этот метод возвращает **двойные** кавычки (»»).  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


---
title: "Метод getCatalogSeparator (SQLServerDatabaseMetaData) | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getCatalogSeparator
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0bbd6842-7210-432a-bef4-e15a63f5cc96
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b5531ae6c62a8e0a588abc136a09e15171074013
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getcatalogseparator-method-sqlserverdatabasemetadata"></a>Метод getCatalogSeparator (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Извлекает **строка** , эта база данных используется в качестве разделителя между каталогом и именем таблицы.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.lang.String getCatalogSeparator()  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект **строка** , содержащее разделитель каталога.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getCatalogSeparator указывается с помощью метода getCatalogSeparator в интерфейсе java.sql.DatabaseMetaData.  
  
 При использовании [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] базы данных, этот метод возвращает символ точки («.») как разделитель каталога.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


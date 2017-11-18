---
title: "Метод getSuperTypes (SQLServerDatabaseMetaData) | Документы Microsoft"
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
- SQLServerDatabaseMetaData.getSuperTypes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5b8e78e6-2bb0-4dc7-9c77-a5609654cb05
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 0891d0d68cea6e84f0f95d23fe5f18497f92549b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="getsupertypes-method-sqlserverdatabasemetadata"></a>Метод getSuperTypes (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Получает описание иерархий определяемых пользователем типов, определенных в заданной схеме этой базы данных.  
  
> [!NOTE]  
>  Этот метод не поддерживается в настоящее время с [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. При использовании этот метод всегда возвращает пустой результирующий набор.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public java.sql.ResultSet getSuperTypes(java.lang.String catalog,  
                                        java.lang.String schemaPattern,  
                                        java.lang.String typeNamePattern)  
```  
  
#### <a name="parameters"></a>Параметры  
 *каталог*  
  
 Объект **строка** , содержащее имя каталога.  
  
 *schemaPattern*  
  
 Объект **строка** , содержащее шаблон имени схемы.  
  
 *tableNamePattern*  
  
 Объект **строка** , содержащее шаблон имени таблицы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) объекта.  
  
## <a name="exceptions"></a>Исключения  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Замечания  
 Этот метод getSuperTypes указывается с помощью метода getSuperTypes в интерфейсе java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>См. также:  
 [Методы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Элементы SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [Класс SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  


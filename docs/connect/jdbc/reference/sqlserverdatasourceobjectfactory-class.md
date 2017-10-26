---
title: "Класс SQLServerDataSourceObjectFactory | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 19f81b3a458ac0fa2d5e276858fcff45eeb0eb4b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="sqlserverdatasourceobjectfactory-class"></a>Класс SQLServerDataSourceObjectFactory
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет фабрику объектов для материализации источников данных из интерфейса JNDI.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** java.lang.Object  
  
 **Реализует:** javax.naming.spi.ObjectFactory  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerDataSourceObjectFactory  
```  
  
## <a name="remarks"></a>Замечания  
 Этот метод наследуется всеми классами источников данных. В рамках поддержки интерфейса Referenceable [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] обеспечивает доступ к этому классу, реализующему ObjectFactory. Серверы приложений Java вызовут getReference класса источника данных, и это будет создан объект ссылки, использующий имя класса внутри себя в качестве своей фабрики класса.  
  
 Если сервер приложений Java для разыменования ссылок объекта, он создает экземпляр SQLServerDataSourceObjectFactory объекта и вызывает [getObjectInstance](../../../connect/jdbc/reference/getobjectinstance-method-sqlserverdatasourceobjectfactory.md) метод, передавая объект ссылки на получить экземпляр источника данных.  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  


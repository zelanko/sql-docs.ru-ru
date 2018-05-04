---
title: Класс SQLServerDataSourceObjectFactory | Документы Microsoft
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
ms.assetid: b616632b-5987-470d-b36c-b22fa9213145
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3b8d13a403cff4d6b3f955bf560ef17f98eae36d
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
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
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerDataSourceObjectFactory](../../../connect/jdbc/reference/sqlserverdatasourceobjectfactory-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

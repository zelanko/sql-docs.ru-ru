---
title: Класс SQLServerConnectionPoolDataSource | Документы Microsoft
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
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ee63cd7614773b63ccab4f95b5019616dab3e400
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="sqlserverconnectionpooldatasource-class"></a>Класс SQLServerConnectionPoolDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Представляет физические подключение к базе данных для диспетчеров пулов соединений.  
  
 **Пакет:** com.microsoft.sqlserver.jdbc  
  
 **Расширяет:** [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
 **Реализует:** javax.sql.ConnectionPoolDataSource  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
public class SQLServerConnectionPoolDataSource  
```  
  
## <a name="remarks"></a>Замечания  
 SQLServerConnectionPoolDataSource обычно используется в средах Java Application Server, поддерживающих встроенные пулы соединений и требующих ConnectionPoolDataSource для установки физических соединений, например на платформе Java, Enterprise Edition (Java Организация пулов соединений по спецификациям EE) серверы приложений, которые предоставляют API-интерфейса JDBC 3.0.  
  
## <a name="see-also"></a>См. также  
 [Элементы SQLServerConnectionPoolDataSource](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Справочник по API для драйвера JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  

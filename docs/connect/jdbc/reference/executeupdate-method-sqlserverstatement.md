---
title: "Метод executeUpdate (SQLServerStatement) | Документы Microsoft"
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
- SQLServerStatement.executeUpdate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10ae662a-ce3c-4b24-875c-5c2df319d93b
caps.latest.revision: 16
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 09479ee3af274d06564427c4ca60f3cc15f36644
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="executeupdate-method-sqlserverstatement"></a>Метод executeUpdate (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE или DELETE; или инструкция SQL, не возвращающая значений, например инструкция SQL DDL. Начиная с версии [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] версии 3.0 драйвера JDBC, метод executeUpdate возвращает правильное количество строк, обновленных в операции СЛИЯНИЯ.  
  
## <a name="overload-list"></a>Список перегрузок  
  
|Имя|Description|  
|----------|-----------------|  
|[executeUpdate (java.lang.String)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-sqlserverstatement.md)|Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE, DELETE или MERGE, либо инструкцию SQL, не возвращающую значения, например инструкцию SQL DDL.|  
|[executeUpdate (java.lang.String, int)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-int.md)|Выполняет заданную инструкцию SQL и сигналы [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с помощью определенного флага о том, следует ли автоматически сформированные ключи, созданного этим [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) объекта должны быть доступны для загрузки.|  
|[executeUpdate (java.lang.String, int &#91; &#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string.md)|Выполняет заданную инструкцию SQL и сообщает драйверу JDBC о доступности автоматически сформированных ключей, указанных в заданном массиве.|  
|[executeUpdate (java.lang.String, java.lang.String &#91; &#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-java-lang-string.md)|Выполняет заданную инструкцию SQL и сообщает драйверу JDBC о доступности автоматически сформированных ключей, указанных в заданном массиве.|  
  
## <a name="see-also"></a>См. также:  
 [Члены SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

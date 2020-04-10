---
title: Метод executeUpdate (SQLServerStatement) | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.executeUpdate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10ae662a-ce3c-4b24-875c-5c2df319d93b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b05edbe0137ad17c5bc667ac39e10c75b958c647
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/08/2020
ms.locfileid: "80924250"
---
# <a name="executeupdate-method-sqlserverstatement"></a>Метод executeUpdate (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE или DELETE; или инструкция SQL, не возвращающая значений, например инструкция SQL DDL. Начиная с [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0, метод executeUpdate возвращает правильное количество строк, обновленных в операции MERGE.  
  
## <a name="overload-list"></a>Список перегрузок  
  
|Имя|Description|  
|----------|-----------------|  
|[executeUpdate (java.lang.String)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-sqlserverstatement.md)|Выполняет заданную инструкцию SQL, которой может быть инструкция INSERT, UPDATE, DELETE или MERGE, либо инструкцию SQL, не возвращающую значения, например инструкцию SQL DDL.|  
|[executeUpdate (java.lang.String, int)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-int.md)|Выполняет заданную инструкцию SQL и уведомляет [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] с помощью заданного флага о том, что автоматически сформированные ключи, созданные этим объектом [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md), должны быть доступны для получения.|  
|[executeUpdate (java.lang.String, int&#91;&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string.md)|Выполняет заданную инструкцию SQL и сообщает драйверу JDBC о доступности автоматически сформированных ключей, указанных в заданном массиве.|  
|[executeUpdate (java.lang.String, java.lang.String&#91;&#93;)](../../../connect/jdbc/reference/executeupdate-method-java-lang-string-java-lang-string.md)|Выполняет заданную инструкцию SQL и сообщает драйверу JDBC о доступности автоматически сформированных ключей, указанных в заданном массиве.|  
  
## <a name="see-also"></a>См. также:  
 [Элементы SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [Класс SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  

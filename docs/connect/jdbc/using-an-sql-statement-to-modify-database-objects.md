---
title: "С помощью инструкции SQL для изменения объектов базы данных | Документы Microsoft"
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
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d5b94ff83ef6cea934efb66f6efb9394d2fa2501
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Использование инструкции SQL для изменения объектов баз данных 
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Чтобы изменить [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] объектов базы данных с помощью инструкции SQL, можно использовать [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Метод executeUpdate передаст инструкцию SQL в базу данных для обработки и возвращается значение 0, так как строки не были затронуты.  
  
 Чтобы сделать это, необходимо сначала создать объект SQLServerStatement с помощью [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
> [!NOTE]  
>  Инструкции SQL, изменяющие объекты в базе данных, называются инструкциями языка описания данных DDL. Они включают такие инструкции, как CREATE TABLE, DROP TABLE, CREATE INDEX и DROP INDEX. Дополнительные сведения о типах инструкций DDL, которые поддерживаются [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], в разделе [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] электронной документации.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, создается инструкция SQL, создаст простую таблицу TestTable в базе данных, инструкция выполняется и выводится возвращаемое значение.  
  
 [!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  


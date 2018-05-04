---
title: Выполнение пакетных операций | Документы Microsoft
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
ms.assetid: 1a576d95-7da6-4b7b-8b32-59e5b4d354c4
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cc71b8b547be9a8b5e62e213d1da4cb8b261837
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="performing-batch-operations"></a>Выполнение пакетных операций
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Для повышения производительности при выполнении нескольких обновлений [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных в случае возникновения [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предоставляет возможность передать несколько обновлений в едином фрагменте работы, который также называют пакета.  
  
 [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) классы все используется для передачи пакетных обновлений. [AddBatch](../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md) метод используется для добавления команды. [ClearBatch](../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md) метод используется для очистки списка команд. [ExecuteBatch](../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md) метод используется для передачи всех команд для обработки. В качестве части пакета могут выполняться только инструкции языка описания данных DDL и языка обработки данных DML, возвращающие простой счетчик обновлений.  
  
 Метод executeBatch возвращает массив **int** значений, соответствующих счетчику обновлений каждой команды. В случае сбоя одного из команд создается BatchUpdateException и следует использовать метод getUpdateCounts класса BatchUpdateException для извлечения массива счетчиков обновления. При возникновении ошибки выполнения команды драйвер продолжает обработку остальных команд. Однако при наличии ошибки синтаксиса в команде происходит ошибка инструкций в пакете.  
  
> [!NOTE]  
>  Если у вас счетчики обновлений, можно сначала отправить инструкцию SET NOCOUNT ON для [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Это позволит уменьшить объем сетевого трафика и увеличить производительность приложений.  
  
 Например, создайте следующую таблицу в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод addBatch используется для создания выполняемых инструкций и метод executeBatch вызывается для отправки пакета в базе данных.  
  
```  
public static void executeBatchUpdate(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('X', 100)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Y', 200)");  
      stmt.addBatch("INSERT INTO TestTable (Col2, Col3) VALUES ('Z', 300)");  
      int[] updateCounts = stmt.executeBatch();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

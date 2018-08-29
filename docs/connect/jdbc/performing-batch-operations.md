---
title: Выполнение пакетных операций | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 1a576d95-7da6-4b7b-8b32-59e5b4d354c4
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39596d1bc481005606a7442d755b3cc9a1ec668b
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2018
ms.locfileid: "42786526"
---
# <a name="performing-batch-operations"></a>Выполнение пакетных операций
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Чтобы обеспечить повышение производительности при выполнении нескольких обновлений базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] позволяет передать несколько обновлений в едином фрагменте работы, который называется пакетом.  
  
 Для передачи пакетных обновлений можно использовать следующие классы: [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) и [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). Метод [addBatch](../../connect/jdbc/reference/addbatch-method-sqlserverpreparedstatement.md) используется для добавления команды. Метод [clearBatch](../../connect/jdbc/reference/clearbatch-method-sqlserverpreparedstatement.md) используется для очистки списка команд. Метод [executeBatch](../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md) используется для передачи всех команд для обработки. В качестве части пакета могут выполняться только инструкции языка описания данных DDL и языка обработки данных DML, возвращающие простой счетчик обновлений.  
  
 Метод executeBatch возвращает массив значений **int**, соответствующих счетчику обновлений каждой команды. В случае сбоя одного из команд создается BatchUpdateException и следует использовать метод getUpdateCounts BatchUpdateException класса для извлечения массива счетчиков обновления. При возникновении ошибки выполнения команды драйвер продолжает обработку остальных команд. Однако при наличии ошибки синтаксиса в команде происходит ошибка инструкций в пакете.  
  
> [!NOTE]  
>  Если отсутствуют счетчики обновлений, можно сначала отправить инструкцию SET NOCOUNT ON [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Это позволит уменьшить объем сетевого трафика и увеличить производительность приложений.  
  
 Для примера создайте в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] следующую таблицу:  
  
```sql
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 В следующем примере открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию, метод addBatch используется для создания выполняемых инструкций, а метод executeBatch вызывается для передачи пакета базе данных.  
  
```java
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
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

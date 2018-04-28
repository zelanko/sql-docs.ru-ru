---
title: С помощью хранимой процедуры с входными параметрами | Документы Microsoft
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
ms.topic: article
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 64bf5a293cbe0f9fd9287a03084d66044a54337a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>Использование хранимых процедур с входными параметрами
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранимой процедуры, который можно вызвать то, которое содержит один или более параметров, которые являются параметры, которые можно использовать для передачи данных в хранимую процедуру. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класс, который можно использовать для вызова хранимых процедур такого вида и обработки данных, он возвращает.  
  
 При использовании драйвера JDBC для вызова хранимой процедуры с ПАРАМЕТРАМИ, необходимо использовать `call` escape-последовательность SQL вместе с [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. Синтаксис `call` escape-последовательность с ПАРАМЕТРАМИ — следующим образом:  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью Escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 При построении `call` escape-последовательности, укажите параметры IN, с помощью? (символ вопросительного знака (?)). Этот символ выполняет роль заполнителя для значений параметра, которые будут переданы хранимой процедуре. Чтобы задать значение для параметра, можно использовать один из методов задания класса SQLServerPreparedStatement. Метод задания, который можно использовать, определяется типом данных параметра IN.  
  
 Во время передачи значения методу задания следует указать не только фактическое значение, которое будет использоваться в параметре, но также порядковый номер параметра в хранимой процедуре. Например, если хранимая процедура содержит единственный параметр IN, его порядковый номер будет 1. Если хранимая процедура содержит два параметра, порядковый номер первого значения будет 1, а второго — 2.  
  
 В качестве примера того, как вызвать хранимую процедуру, которая содержит параметр IN, используйте хранимую процедуру uspGetEmployeeManagers в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных. Эта хранимая процедура принимает один параметр входных данных с именем EmployeeID, который является целым значением, и возвращает рекурсивный список служащих и их менеджеров на основе указанного EmployeeID. Ниже приводится код Java для вызова этой хранимой процедуры.  
  
```  
public static void executeSprocInParams(Connection con) {  
   try {  
      PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}");  
      pstmt.setInt(1, 50);  
      ResultSet rs = pstmt.executeQuery();  
  
      while (rs.next()) {  
         System.out.println("EMPLOYEE:");  
         System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
         System.out.println("MANAGER:");  
         System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
         System.out.println();  
      }  
      rs.close();  
      pstmt.close();  
   }  
  
   catch (Exception e) {  
      e.printStackTrace();  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

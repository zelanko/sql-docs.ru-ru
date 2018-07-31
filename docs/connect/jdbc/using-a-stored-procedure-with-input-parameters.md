---
title: Использование хранимой процедуры с входными параметрами | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 8f491b70-7d1b-42bd-964f-9a8b86af5eaa
caps.latest.revision: 21
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c408fc703a3f6d9831cae226ce858b1a20a80c7
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278775"
---
# <a name="using-a-stored-procedure-with-input-parameters"></a>Использование хранимых процедур с входными параметрами
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Хранимая процедура [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], которую можно вызвать, содержит один или несколько параметров IN, то есть параметров, которые могут быть использованы для передачи данных в хранимую процедуру. В [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предусмотрен класс [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md), который может быть использован для вызова этого вида хранимых процедур и обработки возвращаемых ими данных.  
  
 При использовании драйвера JDBC для вызова хранимой процедуры с параметрами IN следует использовать escape-последовательность SQL `call` вместе с методом [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Ниже приводится синтаксис escape-последовательности `call` с параметрами IN.  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 При создании escape-последовательности `call` укажите параметры IN при помощи (символ вопросительного знака (?)). Этот символ выполняет роль заполнителя для значений параметра, которые будут переданы хранимой процедуре. Чтобы задать значение для параметра, можно использовать один из методов задания класса SQLServerPreparedStatement. Метод задания, который можно использовать, определяется типом данных параметра IN.  
  
 Во время передачи значения методу задания следует указать не только фактическое значение, которое будет использоваться в параметре, но также порядковый номер параметра в хранимой процедуре. Например, если хранимая процедура содержит единственный параметр IN, его порядковый номер будет 1. Если хранимая процедура содержит два параметра, порядковый номер первого значения будет 1, а второго — 2.  
  
 В качестве примера вызова хранимой процедуры, содержащей параметр IN, используйте хранимую процедуру uspGetEmployeeManagers в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]. Эта хранимая процедура принимает один параметр входных данных с именем EmployeeID, который является целым значением, и возвращает рекурсивный список служащих и их менеджеров на основе указанного EmployeeID. Ниже приводится код Java для вызова этой хранимой процедуры.  
  
```java
public static void executeSprocInParams(Connection con) throws SQLException {  
    try(PreparedStatement pstmt = con.prepareStatement("{call dbo.uspGetEmployeeManagers(?)}"); ) {  

        pstmt.setInt(1, 50);  
        ResultSet rs = pstmt.executeQuery();  

        while (rs.next()) {  
            System.out.println("EMPLOYEE:");  
            System.out.println(rs.getString("LastName") + ", " + rs.getString("FirstName"));  
            System.out.println("MANAGER:");  
            System.out.println(rs.getString("ManagerLastName") + ", " + rs.getString("ManagerFirstName"));  
            System.out.println();  
        }  
    }
}
```  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

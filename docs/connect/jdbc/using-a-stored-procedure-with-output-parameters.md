---
title: С помощью хранимой процедуры с выходными параметрами | Документы Microsoft
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
ms.assetid: 1c006f27-7e99-43d5-974c-7b782659290c
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Active
ms.openlocfilehash: adc77f65d20f409d0ad2ff115031d02888876863
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-a-stored-procedure-with-output-parameters"></a>Использование хранимых процедур с выходными параметрами
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] является хранимая процедура, которую можно вызвать, возвращающая один или несколько ВЫХОДНЫХ параметров, которые являются параметрами, которые хранимая процедура используется для возврата данных обратно вызывающему приложению. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класс, который можно использовать для вызова хранимых процедур такого вида и обработки данных, он возвращает.  
  
 При вызове хранимой процедуры этого типа с помощью драйвера JDBC, необходимо использовать `call` escape-последовательность SQL вместе с [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса. Синтаксис `call` escape-последовательности с параметрами OUT необходимо указать в следующем:  
  
 `{call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью Escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 При построении `call` escape-последовательности, укажите параметры OUT с помощью? (символ вопросительного знака (?)). Этот символ выполняет роль заполнителя для значений параметра, которые будут возвращены из хранимой процедуры. Чтобы задать значение для параметра OUT, необходимо указать тип данных каждого параметра с помощью [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) метод класса SQLServerCallableStatement до выполнения хранимой процедуры.  
  
 Значение, указанное для параметра OUT в методе registerOutParameter должен быть один из типов данных JDBC, содержащихся в java.sql.Types, который в свою очередь сопоставляется с одним из собственных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных. Дополнительные сведения о JDBC и [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типов данных в разделе [основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).  
  
 При передаче значения методу registerOutParameter для параметра OUT, укажите для параметра, но также порядковый номер параметра или имени параметра в хранимой процедуре не только тип данных. Например, если в хранимой процедуре имеется один параметр OUT, то первое порядковое значение будет 1, а второе порядковое значение — 2.  
  
> [!NOTE]  
>  Драйвер JDBC не поддерживает использование КУРСОРА, SQLVARIANT, таблицы и отметка времени [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] типы данных в качестве параметров OUT.  
  
 Например, создайте следующую хранимую процедуру в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных:  
  
```  
CREATE PROCEDURE GetImmediateManager  
   @employeeID INT,  
   @managerID INT OUTPUT  
AS  
BEGIN  
   SELECT @managerID = ManagerID   
   FROM HumanResources.Employee   
   WHERE EmployeeID = @employeeID  
END  
```  
  
 Эта хранимая процедура возвращает один параметр OUT (managerID), являющийся целым числом, на основе указанного параметра IN (employeeID), которое также является целым числом. Значение, возвращаемое в параметре OUT, представляет собой ManagerID, основанный на EmployeeID, который содержится в таблице HumanResources.Employee.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию и [выполнение](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод используется для вызова хранимой процедуры GetImmediateManager:  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
      CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");  
      cstmt.setInt(1, 5);  
      cstmt.registerOutParameter(2, java.sql.Types.INTEGER);  
      cstmt.execute();  
      System.out.println("MANAGER ID: " + cstmt.getInt(2));  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
 В примере для определения параметров используются порядковые местоположения. Или можно определить параметр при использовании имени вместо порядкового местоположения. В следующем примере кода изменяется предыдущий пример для иллюстрации использования именованных параметров в приложении Java. Обратите внимание, что имена параметров соответствуют именам параметров в определении хранимой процедуры:  
  
```  
public static void executeStoredProcedure(Connection con) {  
   try {  
      CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");  
      cstmt.setInt("employeeID", 5);  
      cstmt.registerOutParameter("managerID", java.sql.Types.INTEGER);  
      cstmt.execute();  
      System.out.println("MANAGER ID: " + cstmt.getInt("managerID"));  
      cstmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
```  
  
 }  
  
> [!NOTE]  
>  Чтобы выполнить хранимую процедуру в этих примерах используются метод execute класса SQLServerCallableStatement. Он используется, поскольку хранимая процедура не возвратила результирующий набор. В противном случае [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) метод будет использоваться.  
  
 Хранимые процедуры могут возвращать счетчики обновлений и несколько результирующих наборов. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Соответствует спецификации JDBC 3.0, которая определяет, что несколько результирующих наборов и счетчиков обновления должны быть получены до извлечения параметров OUT. Т. е приложение должно получить все объекты результирующего набора и счетчики обновления до извлечения параметров OUT с помощью методов CallableStatement.getter. В противном случае результирующий набор объекты и счетчики обновления, которые уже не были получены будут потеряны при ИЗВЛЕЧЕНИИ параметров. Дополнительные сведения о счетчиках обновлений и несколько результирующих наборов см. в разделе [с помощью хранимой процедуры с числом обновление](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) и [с помощью нескольких результирующих наборов](../../connect/jdbc/using-multiple-result-sets.md).  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

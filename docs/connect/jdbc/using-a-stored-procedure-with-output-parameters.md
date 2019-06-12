---
title: Использование хранимой процедуры с параметрами вывода | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1c006f27-7e99-43d5-974c-7b782659290c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4af5769f5187fd70387f89aebf07625117da9a49
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790338"
---
# <a name="using-a-stored-procedure-with-output-parameters"></a>Использование хранимых процедур с выходными параметрами

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Вызываемая хранимая процедура [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] — это процедура, возвращающая один или несколько параметров OUT, т. е. параметров, используемых хранимой процедурой для возврата данных вызывающему приложению. Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] содержит класс [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md), который может быть использован для вызова этого типа хранимых процедур и обработки возвращаемых ими данных.

При вызове хранимой процедуры этого типа с помощью драйвера JDBC следует использовать escape-последовательность SQL `call` совместно с методом [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Ниже приводится синтаксис escape-последовательности `call` с параметрами OUT:

`{call procedure-name[([parameter][,[parameter]]...)]}`

> [!NOTE]  
> Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).

При создании escape-последовательности `call` укажите параметры OUT при помощи символа "?". (символ вопросительного знака (?)). Этот символ выполняет роль заполнителя для значений параметра, которые будут возвращены из хранимой процедуры. Чтобы указать значение параметра OUT, необходимо указать тип данных всех параметров с помощью метода [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) класса SQLServerCallableStatement до выполнения хранимой процедуры.

Значение, указываемое для параметра OUT в методе registerOutParameter, должно представлять собой один из типов данных JDBC, содержащихся в java.sql.Types, который, в свою очередь, выполняет сопоставление с одним из собственных типов данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Дополнительные сведения о JDBC и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] типов данных, см. в разделе [основные сведения о типах данных драйвера JDBC](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md).

При передаче значения методу registerOutParameter для параметра OUT необходимо указать не только тип данных, который будет использоваться для параметра, но также порядковое размещение или имя параметра в хранимой процедуре. Например, если в хранимой процедуре имеется один параметр OUT, то первое порядковое значение будет 1, а второе порядковое значение — 2.

> [!NOTE]  
> Драйвер JDBC не поддерживает использование типов данных CURSOR, SQLVARIANT, TABLE и TIMESTAMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в качестве параметров OUT.

Для примера создайте следующую хранимую процедуру в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:

```sql
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

В следующем примере открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию, а метод [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) используется для вызова хранимой процедуры GetImmediateManager:

```java
public static void executeStoredProcedure(Connection con) throws SQLException {  
    try(CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}");) {  
        cstmt.setInt(1, 5);  
        cstmt.registerOutParameter(2, java.sql.Types.INTEGER);  
        cstmt.execute();  
        System.out.println("MANAGER ID: " + cstmt.getInt(2));  
    }  
}
```

В примере для определения параметров используются порядковые местоположения. Или можно определить параметр при использовании имени вместо порядкового местоположения. В следующем примере кода изменяется предыдущий пример для иллюстрации использования именованных параметров в приложении Java. Обратите внимание, что имена параметров соответствуют именам параметров в определении хранимой процедуры:

```java
public static void executeStoredProcedure(Connection con) throws SQLException {  
    try(CallableStatement cstmt = con.prepareCall("{call dbo.GetImmediateManager(?, ?)}"); ) {  
        cstmt.setInt("employeeID", 5);  
        cstmt.registerOutParameter("managerID", java.sql.Types.INTEGER);  
        cstmt.execute();  
        System.out.println("MANAGER ID: " + cstmt.getInt("managerID"));  
    }  
}
```

> [!NOTE]  
> Для выполнения хранимой процедуры в этих примерах используется метод execute класса SQLServerCallableStatement. Он используется, поскольку хранимая процедура не возвратила результирующий набор. Если она возвратила результирующий набор, будет использован метод [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md).

Хранимые процедуры могут возвращать счетчики обновлений и несколько результирующих наборов. Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] соответствует спецификации JDBC 3.0, которая определяет, что множественные результирующие наборы и счетчики обновления должны быть получены до получения параметров OUT. То есть приложение извлекает все объекты, результирующий набор и счетчики обновления до извлечения параметров OUT с помощью методов CallableStatement.getter. В противном случае объекты ResultSet и счетчики обновления, которые не были извлечены, будут потеряны при извлечении параметров OUT. Дополнительные сведения о счетчиках обновлений и несколько результирующих наборов, см. в разделе [использование хранимых процедур со счетчиком обновления](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md) и [с помощью нескольких результирующих наборов](../../connect/jdbc/using-multiple-result-sets.md).

## <a name="see-also"></a>См. также:

[Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)

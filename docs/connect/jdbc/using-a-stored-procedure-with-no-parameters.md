---
title: Использование хранимой процедуры без параметров | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d766423b4ee2c1db4b7515c87edfa96b4b84b416
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66790388"
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>Использование хранимых процедур без параметров

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Простейший вид хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которую можно вызвать, представляет собой хранимую процедуру, которая не содержит параметров и возвращает один результирующий набор. Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] содержит класс [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), который может использоваться для вызова такого вида хранимых процедур и обработки возвращаемых ими данных.

При использовании драйвера JDBC для вызова хранимых процедур без параметров необходимо использовать escape-последовательность SQL `call`. Синтаксис escape-последовательности `call` без параметров:

`{call procedure-name}`

> [!NOTE]  
> Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).

Для примера создайте следующую хранимую процедуру в образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:

```sql
CREATE PROCEDURE GetContactFormalNames
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName
   FROM Person.Contact  
END  
```

Эта хранимая процедура возвращает один результирующий набор, который содержит один столбец данных, представляющий собой сочетание названия, имени, фамилии 10 основных контактов, которые хранятся в таблице Person.Contact.

В приведенном ниже примере открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию, а метод [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) используется для вызова хранимой процедуры GetContactFormalNames.

```java
public static void executeSprocNoParams(Connection con) throws SQLException {  
    try(Statement stmt = con.createStatement();) {  

        ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
        while (rs.next()) {  
            System.out.println(rs.getString("FormalName"));  
        }  
    }  
}
```

## <a name="see-also"></a>См. также:

[Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)

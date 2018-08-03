---
title: Использование хранимой процедуры без параметров | Документация Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 157d6f1b3948dbe697afc5af018b197ede9fec9b
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39279135"
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>Использование хранимых процедур без параметров
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Простейший вид хранимой процедуры [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)], которую можно вызвать, представляет собой хранимую процедуру, которая не содержит параметров и возвращает один результирующий набор. Драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] содержит класс [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), который может использоваться для вызова такого вида хранимых процедур и обработки возвращаемых ими данных.  
  
 При использовании драйвера JDBC для вызова хранимых процедур без параметров необходимо использовать escape-последовательность SQL `call`. Синтаксис escape-последовательности `call` без параметров:  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
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
  
  

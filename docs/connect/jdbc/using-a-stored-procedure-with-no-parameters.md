---
title: С помощью хранимой процедуры без параметров | Документы Microsoft
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
ms.assetid: e9470a6d-a758-4c56-96ec-7b37139e36a7
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: bdb24663f0f11ae6bcdb0d24e7d4a9284a8b79d2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-a-stored-procedure-with-no-parameters"></a>Использование хранимых процедур без параметров
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Простейшая форма из [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранимой процедуры, который можно вызвать является та, которая не содержит параметров и возвращает один результирующий набор. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класс, который можно использовать для вызова хранимых процедур такого вида и обработки данных, он возвращает.  
  
 При использовании драйвера JDBC для вызова хранимой процедуры без параметров, необходимо использовать `call` escape-последовательность SQL. Синтаксис `call` escape-последовательность без параметров — следующим образом:  
  
 `{call procedure-name}`  
  
> [!NOTE]  
>  Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью Escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 Например, создайте следующую хранимую процедуру в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных:  
  
```  
CREATE PROCEDURE GetContactFormalNames   
AS  
BEGIN  
   SELECT TOP 10 Title + ' ' + FirstName + ' ' + LastName AS FormalName   
   FROM Person.Contact  
END  
```  
  
 Эта хранимая процедура возвращает один результирующий набор, который содержит один столбец данных, представляющий собой сочетание названия, имени, фамилии десятка лучших контактов, которые хранятся в таблице Person.Contact.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию и [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) метод используется для вызова хранимой процедуры GetContactFormalNames.  
  
```  
public static void executeSprocNoParams(Connection con) {  
   try {  
      Statement stmt = con.createStatement();  
      ResultSet rs = stmt.executeQuery("{call dbo.GetContactFormalNames}");  
  
      while (rs.next()) {  
         System.out.println(rs.getString("FormalName"));  
      }  
      rs.close();  
      stmt.close();  
   }  
   catch (Exception e) {  
      e.printStackTrace();  
   }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

---
title: "Использование хранимых процедур со счетчиком обновлений | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: "26"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3d0d09c7db3e657630515d1c8b9601c1049babdd
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/18/2017
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Использование хранимых процедур со счетчиком обновлений
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Чтобы изменить данные в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью хранимой процедуры, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предоставляет [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класса. С помощью класса SQLServerCallableStatement, можно вызывать хранимые процедуры, которые изменяют данные, содержащиеся в базе данных и возвращать показатель числа обработанных строк, также называется счетчиком обновления.  
  
 После настройки вызова хранимой процедуры с помощью класса SQLServerCallableStatement, затем можно вызвать хранимую процедуру с помощью [выполнение](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) или [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) метод. Метод executeUpdate возвращает **int** не содержит значение, содержащее количество строк, затронутых инструкцией хранимой процедуры, но метод execute. Если метод execute и данные для подсчета числа обработанных строк, можно вызвать [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) метод после выполнения хранимой процедуры.  
  
> [!NOTE]  
>  Чтобы драйвер JDBC возвращал все счетчики обновления, включая счетчики, возвращенные сработавшими триггерами, установите свойство lastUpdateCount строки подключения в значение false. Дополнительные сведения о свойстве lastUpdateCount см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 В качестве примера создайте следующую таблицу и хранимую процедуру, а также вставьте образец данных в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных:  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
  
CREATE PROCEDURE UpdateTestTable  
   @Col2 varchar(50),  
   @Col3 int  
AS  
BEGIN  
   UPDATE TestTable  
   SET Col2 = @Col2, Col3 = @Col3  
END;  
INSERT INTO dbo.TestTable (Col2, Col3) VALUES ('b', 10);  
```  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод execute используется для вызова хранимой процедуры UpdateTestTable и затем используется метод getUpdateCount для возврата количества строк, которые являются Хранимая процедура влияет на.  
  
 [!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

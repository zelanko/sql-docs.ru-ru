---
title: Использование хранимых процедур со счетчиком обновлений | Документы Майкрософт
ms.custom: ''
ms.date: 07/11/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64cf4877-5995-4bfc-8865-b7618a5c8d01
caps.latest.revision: 26
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b840cc9b6b8492af0cffa71986d747ac59b7dd57
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278925"
---
# <a name="using-a-stored-procedure-with-an-update-count"></a>Использование хранимых процедур со счетчиком обновлений
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Для изменения данных в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] с помощью хранимой процедуры в драйвере [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предусмотрен класс [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md). С помощью класса SQLServerCallableStatement можно вызывать хранимые процедуры, которые изменяют данные в базе данных и возвращают количество обработанных строк, которое также называется счетчиком обновления.  
  
 После настройки вызова хранимой процедуры с помощью класса SQLServerCallableStatement можно вызывать эту хранимую процедуру с помощью метода [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) или [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md). Метод executeUpdate возвращает значение **int**, которое содержит количество строк, обработанных хранимой процедурой, а метод execute не возвращает это значение. Если используется метод execute и нужно получить количество обработанных строк, можно вызвать метод [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) после выполнения хранимой процедуры.  
  
> [!NOTE]  
>  Чтобы драйвер JDBC возвращал все счетчики обновления, включая счетчики, возвращенные сработавшими триггерами, установите свойство lastUpdateCount строки подключения в значение false. Дополнительные сведения о свойстве lastUpdateCount см. в разделе [заданию свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
 В качестве примера создайте следующую таблицу и хранимую процедуру, а также вставьте образец данных в образец базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]:  
  
```sql
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
  
 В приведенном ниже примере в функцию передается открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], метод execute используется для вызова хранимой процедуры UpdateTestTable, а затем метод getUpdateCount возвращает количество строк, обработанных хранимой процедурой.  
  
 [!code[JDBC#UsingSprocWithUpdateCount1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_0_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  

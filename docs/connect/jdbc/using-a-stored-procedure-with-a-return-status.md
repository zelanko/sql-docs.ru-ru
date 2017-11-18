---
title: "Использование хранимых процедур с состояниями возврата | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b126e95-8458-41d6-af37-fc6662859f19
caps.latest.revision: 22
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8247f7f81e70aafac8d109abe7f8303c8e13f487
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-a-stored-procedure-with-a-return-status"></a>Использование хранимых процедур с состояниями возврата
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Объект [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранимой процедуры, который можно вызвать то, которое возвращает статус или параметр результата. Обычно используется для указания успешного выполнения или ошибки хранимой процедуры. [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] Предоставляет [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) класс, который можно использовать для вызова хранимых процедур такого вида и обработки данных, он возвращает.  
  
 При вызове хранимой процедуры этого типа с помощью драйвера JDBC, необходимо использовать `call` escape-последовательность SQL совместно с [prepareCall](../../connect/jdbc/reference/preparecall-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса . Синтаксис `call` escape-последовательности с возвращаемого параметра состояния является следующее:  
  
 `{[?=]call procedure-name[([parameter][,[parameter]]...)]}`  
  
> [!NOTE]  
>  Дополнительные сведения об escape-последовательностях SQL см. в разделе [с помощью Escape-последовательностей SQL](../../connect/jdbc/using-sql-escape-sequences.md).  
  
 При построении `call` escape-последовательности, укажите с помощью возвращаемого параметра состояния? (символ вопросительного знака (?)). Этот символ выполняет роль заполнителя для значения параметра, которое будет возвращено из хранимой процедуры. Чтобы задать значение для возвращаемого параметра состояния, необходимо указать тип данных параметра с помощью [registerOutParameter](../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md) метод класса SQLServerCallableStatement до выполнения хранимой процедуры.  
  
> [!NOTE]  
>  При использовании драйвера JDBC с базой данных SQL Server, указываемое для возвращаемого параметра состояния в методе registerOutParameter значение всегда будет целым числом, который можно задать с помощью типа данных java.sql.Types.INTEGER.  
  
 Кроме того при передаче значения методу registerOutParameter для возвращаемого параметра состояния, должен содержаться не только тип данных для параметра, но также порядковый номер параметра в вызове хранимой процедуры. Порядковое местоположение возвращаемого параметра состояния всегда будет 1, поскольку этот параметр всегда является первым в вызове в хранимой процедуры. Несмотря на то, что класс SQLServerCallableStatement предоставляет поддержку для указания определенного параметра с помощью имени параметра, для возвращаемых параметров состояния можно использовать только порядковый номер параметра.  
  
 Например, создайте следующую хранимую процедуру в [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных:  
  
```  
CREATE PROCEDURE CheckContactCity  
   (@cityName CHAR(50))  
AS  
BEGIN  
   IF ((SELECT COUNT(*)  
   FROM Person.Address  
   WHERE City = @cityName) > 1)  
   RETURN 1  
ELSE  
   RETURN 0  
END  
```  
  
 Эта хранимая процедура возвращает значение состояния 1 или 0, в зависимости от того, включен ли город, указанный в параметре cityName, в таблицу Person.Address.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию и [выполнение](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод используется для вызова хранимой процедуры CheckContactCity:  
  
 [!code[JDBC#UsingSprocWithReturnStatus1](../../connect/jdbc/codesnippet/Java/using-a-stored-procedure_1_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с хранимыми процедурами](../../connect/jdbc/using-statements-with-stored-procedures.md)  
  
  


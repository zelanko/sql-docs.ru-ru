---
title: "Изменение данных с помощью инструкции SQL | Документы Microsoft"
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
ms.assetid: 4704199b-c0ae-4c77-8a2e-6963715b4ffb
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e913a81f88140c983836d4231ed9c926857f0c14
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-an-sql-statement-to-modify-data"></a>Использование инструкции SQL для изменения данных
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Чтобы изменить данные, содержащиеся в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью инструкции SQL, можно использовать [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Метод executeUpdate передаст инструкцию SQL в базу данных для обработки и затем возвращает значение, указывающее число затронутых строк.  
  
 Чтобы сделать это, необходимо сначала создать объект SQLServerStatement с помощью [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, составляется инструкция SQL, добавляет новые данные в таблицу и инструкция выполняется и выводится возвращаемое значение.  
  
 [!code[JDBC#UsingSQLToModifyData1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_1_1.java)]  
  
> [!NOTE]  
>  Если необходимо использовать инструкцию SQL, который содержит параметры для изменения данных в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных, следует использовать [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md) метод [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса.  
>   
>  Если столбец, в который делается попытка вставить данные, содержит специальные знаки, такие как пробелы, необходимо задать вставляемые значения, даже если это значения по умолчанию. Если этого не сделать, операция вставки закончится ошибкой.  
>   
>  Чтобы драйвер JDBC возвращал все счетчики обновления, включая счетчики, возвращенные сработавшими триггерами, установите свойство lastUpdateCount строки подключения в значение false. Дополнительные сведения о свойстве lastUpdateCount см. в разделе [задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  


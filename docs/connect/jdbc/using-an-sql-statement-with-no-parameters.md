---
title: "С помощью инструкции SQL без параметров | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 1e7e97fa030c2efd499aebfa054c0e4827d590dc
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-an-sql-statement-with-no-parameters"></a>Использование инструкции SQL без параметров
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Для работы с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью инструкции SQL, не содержит параметров, можно использовать [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса, чтобы вернуть [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) , будет содержать запрошенные данные. Чтобы сделать это, необходимо сначала создать объект SQLServerStatement с помощью [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, создается и запускается инструкция SQL и затем результаты считываются из результирующего набора.  
  
 [!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]  
  
 Дополнительные сведения об использовании результирующих наборов см. в разделе [управление результирующие наборы с драйвером JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  


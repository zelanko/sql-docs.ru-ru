---
title: С помощью инструкции SQL с параметрами | Документы Microsoft
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
ms.assetid: 3202b88f-ce13-44dd-982c-c6a3b0260378
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 67367fbdd984f0006fd7ed5d4c92d0c696e583a2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="using-an-sql-statement-with-parameters"></a>Использование инструкции SQL с параметрами
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Для работы с данными в [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] базы данных с помощью инструкции SQL, содержащей параметры IN, можно использовать [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverpreparedstatement.md) метод [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) класса, чтобы вернуть [ SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) , будет содержать запрошенные данные. Чтобы сделать это, необходимо сначала создать объект SQLServerPreparedStatement с помощью [prepareStatement](../../connect/jdbc/reference/preparestatement-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) класса.  
  
 При создании инструкции SQL параметры IN определяются с использованием «?» (вопросительного знака), действующего как заполнитель для значений параметров, которые позже будут переданы в инструкцию SQL. Чтобы задать значение для параметра, можно использовать один из методов задания класса SQLServerPreparedStatement. Используемый метод задания определяется типом данных того значения, которое надо передать в инструкцию SQL.  
  
 Во время передачи значения методу задания следует указать не только фактическое значение, которое будет использоваться в инструкции SQL, но также порядковый номер параметра в инструкции SQL. Например, если инструкция SQL содержит единственный параметр, его порядковый номер будет 1. Если инструкция содержит два параметра, порядковый номер первого значения будет 1, а второго — 2.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, Подготовленная инструкция SQL создается и запускается с одним значением параметра строки и затем результаты считываются из результирующего набора.  
  
 [!code[JDBC#UsingSQLWithParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_1_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)  
  
  

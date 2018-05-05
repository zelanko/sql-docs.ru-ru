---
title: Обработка сложных инструкций | Документы Microsoft
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
ms.topic: conceptual
ms.assetid: 6b807a45-a8b5-4b1c-8b7b-d8175c710ce0
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8dc009ed538571d5b66a1240adc8b4c41cbab0a6
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="handling-complex-statements"></a>Обработка сложных инструкций
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)], может потребоваться обработка сложных инструкций, включая инструкции, которые динамически создаются во время выполнения. Сложные инструкции часто выполняют разнообразные задачи, включая обновление, вставку и удаление. Такие типы инструкций также могут возвращать несколько результирующих наборов и выходных параметров. В подобных ситуациях в коде Java, выполняющем инструкции, типы и количество возвращаемых объектов и данных могут быть не известны заранее.  
  
 Для эффективной обработки сложных инструкций драйвер JDBC предоставляет многочисленные методы запроса возвращаемых объектов и данных, что позволяет приложению правильно их обрабатывать. Ключевым моментом в обработки сложных инструкций является [выполнение](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Этот метод возвращает **логическое** значение. Значение true показывает, что первым из инструкции возвращается результирующий набор. Значение false показывает, что первым возвращается количество операций обновления.  
  
 Если известен тип возвращаемого объекта или данных, который был возвращен, можно использовать либо [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) или [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) метод для обработки этих данных. Чтобы перейти на следующий объект или набор данных, возвращаемый сложной инструкцией, можно вызвать [getMoreResults](../../connect/jdbc/reference/getmoreresults-method.md) метод.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, создается сложная инструкция, сочетающая вызов хранимой процедуры с инструкцией SQL, инструкции выполняются, а затем `do` цикл используется для обработки всех результирующие наборы и обновленные значения возвращаются.  
  
 [!code[JDBC#HandlingComplexStatements1](../../connect/jdbc/codesnippet/Java/handling-complex-statements_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

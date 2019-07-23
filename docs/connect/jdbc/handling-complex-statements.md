---
title: Обработка сложных инструкций | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 6b807a45-a8b5-4b1c-8b7b-d8175c710ce0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7adee47147a8aad153bc323470f1711426d92350
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67956546"
---
# <a name="handling-complex-statements"></a>Обработка сложных инструкций
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании драйвера [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] может потребоваться обработка сложных инструкций, включая инструкции, которые динамически создаются во время выполнения. Сложные инструкции часто выполняют разнообразные задачи, включая обновление, вставку и удаление. Такие типы инструкций также могут возвращать несколько результирующих наборов и выходных параметров. В подобных ситуациях в коде Java, выполняющем инструкции, типы и количество возвращаемых объектов и данных могут быть не известны заранее.  
  
 Для эффективной обработки сложных инструкций драйвер JDBC предоставляет многочисленные методы запроса возвращаемых объектов и данных, что позволяет приложению правильно их обрабатывать. Ключевым моментом обработки сложных инструкций является вызов метода [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Этот метод возвращает **логическое** значение. Значение true показывает, что первым из инструкции возвращается результирующий набор. Значение false показывает, что первым возвращается количество операций обновления.  
  
 Если известен тип возвращаемого объекта или данных, то для обработки этих данных можно использовать метод [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) или [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md). Чтобы обработать следующий объект или набор данных, возвращаемый сложной инструкцией, можно вызвать метод [getMoreResults](../../connect/jdbc/reference/getmoreresults-method.md).  
  
 В следующем примере в функцию передается открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], составляется сложная инструкция, сочетающая вызов хранимой процедуры и инструкцию SQL, инструкции выполняются, а затем в цикле `do` обрабатываются все возвращенные результирующие наборы и обновленные значения.  
  
 [!code[JDBC#HandlingComplexStatements1](../../connect/jdbc/codesnippet/Java/handling-complex-statements_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

---
title: Использование метаданных результирующего набора | Документы Microsoft
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
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2b00d44989a4289ed8c6d8bb3d2086732c3aaca
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="using-result-set-metadata"></a>Использование метаданных результирующего набора
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Чтобы запрашивать в результирующем наборе сведения о столбцах, которые она содержит [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) класса. Этот класс содержит многочисленные методы, которые возвращают сведения в виде одного значения.  
  
 Чтобы создать объект SQLServerResultSetMetaData, можно использовать [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод getMetaData класса SQLServerResultSet используется для возврата объекта SQLServerResultSetMetaData, а затем различные методы объекта Объект SQLServerResultSetMetaData используются для отображения сведений об имени и типе данных столбцов, содержащихся в результирующем наборе.  
  
 [!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]  
  
## <a name="see-also"></a>См. также  
 [Обработка метаданных с использованием драйвера JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)  
  
  

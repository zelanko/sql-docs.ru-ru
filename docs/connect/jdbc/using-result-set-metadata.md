---
title: Использование метаданных результирующего набора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d89e8130c897bbf7914b2d3d5d47cba8d38bd01
ms.sourcegitcommit: 2f9cafc1d7a3773a121bdb78a095018c8b7c149f
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39661676"
---
# <a name="using-result-set-metadata"></a>Использование метаданных результирующего набора

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В драйвере [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализован класс [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), позволяющий запрашивать в результирующем наборе сведения о содержащихся в нем столбцах. Этот класс содержит многочисленные методы, которые возвращают сведения в виде одного значения.

Чтобы создать объект SQLServerResultSetMetaData, можно использовать [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса.

В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод getMetaData класса SQLServerResultSet используется для возврата объекта SQLServerResultSetMetaData, а затем различные методы объекта Объект SQLServerResultSetMetaData используются для отображения сведений об имени и типе данных столбцов, содержащихся в результирующем наборе.

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>См. также:

[Обработка метаданных с использованием драйвера JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)

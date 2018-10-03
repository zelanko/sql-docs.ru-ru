---
title: Использование метаданных результирующего набора | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 0e0d42d02d6c288b1d82df6925219ce9787f39b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47728672"
---
# <a name="using-result-set-metadata"></a>Использование метаданных результирующего набора

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

В драйвере [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализован класс [SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md), позволяющий запрашивать в результирующем наборе сведения о содержащихся в нем столбцах. Этот класс содержит многочисленные методы, которые возвращают сведения в виде одного значения.

Чтобы создать объект SQLServerResultSetMetaData, можно использовать [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса.

В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод getMetaData класса SQLServerResultSet используется для возврата объекта SQLServerResultSetMetaData, а затем различные методы объекта Объект SQLServerResultSetMetaData используются для отображения сведений об имени и типе данных столбцов, содержащихся в результирующем наборе.

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>См. также:

[Обработка метаданных с использованием драйвера JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)

---
title: Использование метаданных базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0bad06da093edd83b7df2e1c10f2b68bdca7a210
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798665"
---
# <a name="using-database-metadata"></a>Использование метаданных базы данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Чтобы запросить в базе данных сведения о поддерживаемых функциях, в [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализован класс [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md). Этот класс содержит многочисленные методы, которые возвращают сведения в виде одного значения или результирующего набора.

Чтобы создать объект SQLServerDatabaseMetaData, вы можете использовать метод [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) для получения сведений о базе данных, к которой установлено подключение.

В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию, метод getMetaData класса SQLServerConnection используется для возврата объекта SQLServerDatabaseMetadata, а затем различные методы объекта Объект SQLServerDatabaseMetaData используются для отображения сведений о драйвера, версии драйвера, имени базы данных и версии базы данных.

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>См. также:

[Обработка метаданных с использованием драйвера JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)

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
ms.openlocfilehash: fbe290c558dd8c64605bad0a977657904582c696
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916259"
---
# <a name="using-database-metadata"></a>Использование метаданных базы данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Чтобы запросить в базе данных сведения о поддерживаемых функциях, в [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализован класс [SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md). Этот класс содержит многочисленные методы, которые возвращают сведения в виде одного значения или результирующего набора.

Чтобы создать объект SQLServerDatabaseMetaData, вы можете использовать метод [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) для получения сведений о базе данных, к которой установлено подключение.

В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образцом базы данных передается в функцию, метод GetObject класса SQLServerConnection используется для возврата объекта SQLServerDatabaseMetadata, а затем различные методы класса Объект SQLServerDatabaseMetaData используется для вывода сведений о драйвере, версии драйвера, имени базы данных и версии базы данных.

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>См. также:

[Обработка метаданных с использованием драйвера JDBC](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)

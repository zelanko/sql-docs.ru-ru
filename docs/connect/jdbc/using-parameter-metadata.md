---
title: Использование метаданных параметров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: db2c1957-91c6-4989-a07b-9f8be6d2033a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 168a153ecf12acda5adfbae22d13618669c6c2a4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916216"
---
# <a name="using-parameter-metadata"></a>Использование метаданных о параметрах

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Чтобы запросить у объекта [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md) или [SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) содержащиеся в нем параметры, в [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализован класс [SQLServerParameterMetaData](../../connect/jdbc/reference/sqlserverparametermetadata-class.md). Этот класс содержит многочисленные поля и методы, которые возвращают сведения в виде одного значения.

Чтобы создать объект SQLServerParameterMetaData, можно использовать методы [getParameterMetaData](../../connect/jdbc/reference/getparametermetadata-method-sqlserverpreparedstatement.md) классов SQLServerPreparedStatement и SQLServerCallableStatement.

В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образцом базы данных передается в функцию, метод getParameterMetaData класса SQLServerCallableStatement используется для возврата объекта SQLServerParameterMetaData, а затем для различных методы объекта SQLServerParameterMetaData используются для вывода сведений о типе и режиме параметров, содержащихся в хранимой процедуре HumanResources. uspUpdateEmployeeHireInfo.

[!code[JDBC#UsingParamMetaData1](../../connect/jdbc/codesnippet/Java/using-parameter-metadata_1.java)]  

> [!NOTE]  
> При использовании класса SQLServerParameterMetaData с подготовленными инструкциями существуют некоторые ограничения.
>
> **Для Microsoft JDBC Driver for SQL Server 6.0 (или более поздней версии)** : при использовании SQL Server 2008 или 2008 R2 драйвер JDBC поддерживает инструкции SELECT, DELETE, INSERT и UPDATE при условии, что они не содержат вложенные запросы или соединения.

Запросы MERGE также не поддерживаются для класса SQLServerParameterMetaData при использовании SQL Server 2008 или 2008 R2. Для SQL Server 2012 и более поздних версий поддерживаются метаданные параметров со сложными запросами.

Получение метаданных параметров для зашифрованных столбцов не поддерживается. **Для Microsoft JDBC Driver for SQL Server 4.1 или 4.2**: драйвер JDBC поддерживает инструкции SELECT, DELETE, INSERT и UPDATE при условии, что они не содержат вложенные запросы или соединения. Запросы MERGE также не поддерживаются для класса SQLServerParameterMetaData.

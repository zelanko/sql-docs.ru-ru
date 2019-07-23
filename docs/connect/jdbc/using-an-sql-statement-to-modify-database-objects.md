---
title: Использование инструкции SQL для изменения объектов баз данных | Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 28c71784f8e51600aef111649b12f81b5878b324
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916384"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Использование инструкции SQL для изменения объектов баз данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Для изменения объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием инструкции SQL можно использовать метод [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Метод executeUpdate передаст инструкцию SQL базе данных для обработки, а затем возвратит значение 0, так как не было затронуто ни одной строки.

Для этого сначала нужно создать объект SQLServerStatement с помощью метода [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

> [!NOTE]  
> Инструкции SQL, изменяющие объекты в базе данных, называются инструкциями языка описания данных DDL. К ним относятся такие инструкции `CREATE TABLE`, `DROP TABLE`как `CREATE INDEX`,, `DROP INDEX`и. Дополнительные сведения о типах инструкций DDL, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

В приведенном ниже примере функции передается открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], составляется инструкция SQL, которая создаст простую таблицу TestTable в базе данных, а затем инструкция выполняется, и выводится возвращаемое значение.

[!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]

## <a name="see-also"></a>См. также:

[Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)

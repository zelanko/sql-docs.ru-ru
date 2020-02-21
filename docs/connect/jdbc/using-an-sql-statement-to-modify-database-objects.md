---
title: Использование инструкции SQL для изменения объектов баз данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: f49ea499-df3c-4e85-9fc7-450fb99622a6
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de8e357328c151e3762f324dcbeba2525df53530
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69026565"
---
# <a name="using-an-sql-statement-to-modify-database-objects"></a>Использование инструкции SQL для изменения объектов баз данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Для изменения объектов базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] с использованием инструкции SQL можно использовать метод [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Метод executeUpdate передаст инструкцию SQL базе данных для обработки, а затем возвратит значение 0, так как не было затронуто ни одной строки.

Для этого сначала нужно создать объект SQLServerStatement с помощью метода [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

> [!NOTE]  
> Инструкции SQL, изменяющие объекты в базе данных, называются инструкциями языка описания данных DDL. К ним относятся такие инструкции, как `CREATE TABLE`, `DROP TABLE`, `CREATE INDEX` и `DROP INDEX`. Дополнительные сведения о типах инструкций DDL, поддерживаемых [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], см. в электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

В приведенном ниже примере функции передается открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], составляется инструкция SQL, которая создаст простую таблицу TestTable в базе данных, а затем инструкция выполняется, и выводится возвращаемое значение.

[!code[JDBC#UsingSQLToModifyDBObjects1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_0_1.java)]

## <a name="see-also"></a>См. также раздел

[Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)

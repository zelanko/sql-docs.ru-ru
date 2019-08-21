---
title: Использование инструкции SQL для изменения данных | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4704199b-c0ae-4c77-8a2e-6963715b4ffb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a9de31bad8ef2980e7322b529a6a2b68a12355c2
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69026754"
---
# <a name="using-an-sql-statement-to-modify-data"></a>Использование инструкции SQL для изменения данных

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Для изменения данных, содержащихся в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], с использованием инструкции SQL можно использовать метод [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Метод executeUpdate передаст инструкцию SQL в базу данных для обработки и возвратит значение, показывающее количество затронутых строк.

Для этого сначала нужно создать объект SQLServerStatement с помощью метода [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

В приведенном ниже примере в функцию передается открытое соединение с образцом базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], составляется инструкция SQL, которая добавляет новые данные в таблицу, а затем инструкция выполняется, и выводится возвращаемое значение.

[!code[JDBC#UsingSQLToModifyData1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-t_1_1.java)]

> [!NOTE]  
> Если нужно добавить содержащую параметры инструкцию SQL, чтобы изменить данные в базе данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], следует использовать метод [executeUpdate](../../connect/jdbc/reference/executeupdate-method-sqlserverpreparedstatement.md) класса [SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md).
>
> Если столбец, в который делается попытка вставить данные, содержит специальные знаки, такие как пробелы, необходимо задать вставляемые значения, даже если это значения по умолчанию. Если этого не сделать, операция вставки закончится ошибкой.
>
> Чтобы драйвер JDBC возвращал все счетчики обновления, включая счетчики, возвращенные сработавшими триггерами, установите свойство lastUpdateCount строки подключения в значение false. Дополнительные сведения о свойстве lastUpdateCount см. [в разделе Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md).

## <a name="see-also"></a>См. также раздел

[Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)

---
title: Использование инструкции SQL без параметров | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4b0728bd-059b-4b71-895c-999335bc7427
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6161f70455e5f1c947841d0381ba1a1de3a778a9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006014"
---
# <a name="using-an-sql-statement-with-no-parameters"></a>Использование инструкции SQL без параметров

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Для работы с данными в базе [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] при помощи инструкции SQL, не содержащей параметров, вы можете использовать метод [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md), чтобы возвратить набор [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md), который будет содержать запрошенные данные. Для этого сначала нужно создать объект SQLServerStatement с помощью метода [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md).

В следующем примере в функцию передается открытое подключение к образцу базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], создается и запускается инструкция SQL, а затем результаты считываются из результирующего набора.

[!code[JDBC#UsingSQLWithNoParams1](../../connect/jdbc/codesnippet/Java/using-an-sql-statement-w_0_1.java)]

Дополнительные сведения об использовании результирующих наборов см. [в разделе Управление результирующими наборами с помощью драйвера JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md).

## <a name="see-also"></a>См. также:

[Использование инструкций в SQL](../../connect/jdbc/using-statements-with-sql.md)

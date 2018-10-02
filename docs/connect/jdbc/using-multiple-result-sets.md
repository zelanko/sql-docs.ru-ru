---
title: Использование нескольких результирующих наборов | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fd3294eb5ff9d25b6e5d067249d829b21428035a
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47814712"
---
# <a name="using-multiple-result-sets"></a>Использование нескольких результирующих наборов

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

При работе со встроенным SQL или хранимыми процедурами [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], которые возвращают более одного результирующего набора, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] реализует метод [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) в классе [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) для получения каждого из возвращенных результирующих наборов. Кроме того, при выполнении инструкции, которая возвращает несколько результирующих наборов, можно использовать метод [execute](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) класса SQLServerStatement. Он возвращает **логическое** значение, указывающее, чем является возвращенное значение: результирующим набором или числом обновлений.

Если метод execute возвращает значение **true**, то выполненная инструкция возвратила один или несколько результирующих наборов. Доступ к первому результирующему набору можно получить, вызвав метод getResultSet. Чтобы определить, есть ли еще доступные результирующие наборы, можно вызвать метод [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md), который возвращает **логическое** значение **true**, если доступны также другие результирующие наборы. Если доступно большее число результирующих наборов, можно снова вызвать метод getResultSet, чтобы получить к ним доступ. Эту процедуру можно продолжать до тех пор, пока не будут обработаны все результирующие наборы. Если метод getMoreResults возвращает **false**, существуют больше нет результирующих наборов для процесса.

Если метод execute возвращает **false**, то выполненная инструкция возвратила значение числа обновлений, которое можно получить с помощью метода [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md).

> [!NOTE]  
> Дополнительные сведения о счетчиках обновлений см. в разделе [использование хранимых процедур со счетчиком обновления](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md).

В следующем примере открытое подключение к примеру базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию, и создается инструкция SQL, которая после выполнения возвращает два результирующих набора:

[!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]

В этом случае известно, что количество результирующих наборов равно двум. Но этот код написан таким образом, что даже если количество возвращенных результирующих наборов было бы неизвестно, как при вызове хранимой процедуры, все они были бы обработаны. Пример вызова хранимой процедуры, которая возвращает несколько результирующих наборов наряду со значениями обновления, см. в разделе [Обработка сложных инструкций](../../connect/jdbc/handling-complex-statements.md).

> [!NOTE]  
> Когда вызов метода getMoreResults класса SQLServerStatement, возвращенный ранее результирующий набор неявно закрывается.

## <a name="see-also"></a>См. также:

[Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)

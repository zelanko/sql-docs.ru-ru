---
title: "Использование нескольких результирующих наборов | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab6a3cfa-073b-44e9-afca-a8675cfe5fd1
caps.latest.revision: 33
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e4796d369ed9eb5567cb026d1892399c86479897
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="using-multiple-result-sets"></a>Использование нескольких результирующих наборов
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При работе со встроенным SQL или [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] хранимых процедур, которые возвращают более чем одного результирующего набора, [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] предоставляет [getResultSet](../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) метод в [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса для получение каждого возвращенного набора данных. Кроме того, если выполнение инструкции, которая возвращает несколько результирующих наборов, можно использовать [выполнение](../../connect/jdbc/reference/execute-method-sqlserverstatement.md) метод SQLServerStatement класса, так как он вернет **логическое** значение, указывающее, если Возвращаемое значение является результирующим набором или счетчиком обновлений.  
  
 Если метод execute возвращает **true**, выполненная инструкция возвратила один или несколько результирующих наборов. Можно использовать для первого результирующего набора путем вызова метода getResultSet. Чтобы определить, если доступно несколько результирующих наборов, можно вызвать [getMoreResults](../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md) метод, возвращающий **логическое** значение **true** Если доступны дополнительные результирующие наборы. Если доступно несколько результирующих наборов, можно вызвать метод getResultSet еще раз для доступа к ним, продолжить процесс, пока не будут обработаны все результирующие наборы. Если метод getMoreResults возвращает **false**, существует больше нет результирующих наборов для процесса.  
  
 Если метод execute возвращает **false**, выполненная инструкция возвратила значение счетчика обновлений, которое можно получить, вызвав [getUpdateCount](../../connect/jdbc/reference/getupdatecount-method-sqlserverstatement.md) метод.  
  
> [!NOTE]  
>  Дополнительные сведения о счетчиках обновлений см. в разделе [с помощью хранимой процедуры с числом обновления](../../connect/jdbc/using-a-stored-procedure-with-an-update-count.md).  
  
 В следующем примере открытое соединение с [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных передается в функцию и создается инструкция SQL, при выполнении возвращает два результирующих набора:  
  
 [!code[JDBC#UsingMultipleResultSets1](../../connect/jdbc/codesnippet/Java/using-multiple-result-sets_1.java)]  
  
 В этом случае известно, что количество результирующих наборов равно двум. Но этот код написан таким образом, что даже если количество возвращенных результирующих наборов было бы неизвестно, как при вызове хранимой процедуры, все они были бы обработаны. Пример вызова хранимой процедуры, которая возвращает несколько результирующих наборов наряду со значениями обновления см. в разделе [обработка сложных инструкций](../../connect/jdbc/handling-complex-statements.md).  
  
> [!NOTE]  
>  При вызове в метод getMoreResults класса SQLServerStatement, возвращенный ранее результирующий набор неявно закрывается.  
  
## <a name="see-also"></a>См. также:  
 [Использование инструкций с драйвером JDBC](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  

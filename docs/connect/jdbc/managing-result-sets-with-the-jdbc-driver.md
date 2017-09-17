---
title: "Управление результирующими наборами с драйвером JDBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: e17e39f8a83313a60b269fed82631b80f07ffed5
ms.contentlocale: ru-ru
ms.lasthandoff: 09/09/2017

---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>Управление результирующими наборами с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Результирующий набор — это объект, представляющий набор данных, которые возвращаются из источника данных, как правило в результате запроса. Результирующий набор содержит строки и столбцы, которые хранят запрошенные элементы данных, переход осуществляется при помощи курсора. Результирующий набор может быть обновлен, то есть его можно изменить, а изменения передать исходному источнику данных. Результирующий набор также может иметь несколько уровней чувствительности к переменам в базовом источнике данных.  
  
 Тип результирующего набора определяется при создании инструкции, когда вызов [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) метод [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) классом. Фундаментальная роль результирующего набора заключается в обеспечении приложений Java полезным представлением данных базы данных. Обычно это выполняется посредством введения методов считывания и задания свойств для элементов данных результирующего набора.  
  
 В следующем примере, основанный на [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] образца базы данных, результирующий набор создается путем вызова [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) метод [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md) класса. Данные в результирующем наборе отображается с помощью [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) метод [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md) класса.  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 В подразделах данного раздела приводится описание различных аспектов использования результирующего набора, включая типы курсора, параллелизм и блокировку строк.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Основные сведения о типах курсоров](../../connect/jdbc/understanding-cursor-types.md)|Описывает различные типы курсоров, которые [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] поддерживает.|  
|[Основные сведения о управление параллелизмом](../../connect/jdbc/understanding-concurrency-control.md)|Описывает, как драйвер JDBC поддерживает управление параллелизмом.|  
|[Основные сведения о блокировке строк](../../connect/jdbc/understanding-row-locking.md)|Описывает, как драйвер JDBC поддерживает блокировку строк.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

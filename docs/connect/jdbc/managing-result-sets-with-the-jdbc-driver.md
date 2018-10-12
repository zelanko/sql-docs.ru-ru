---
title: Управление результирующими наборами с помощью драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 49bb2f1743675f1ad381b9a5849cc395a5355d42
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47837722"
---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>Управление результирующими наборами с помощью драйвера JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Результирующий набор — это объект, представляющий набор данных, которые возвращаются из источника данных, как правило в результате запроса. Результирующий набор содержит строки и столбцы, которые хранят запрошенные элементы данных, переход осуществляется при помощи курсора. Результирующий набор может быть обновлен, то есть его можно изменить, а изменения передать исходному источнику данных. Результирующий набор также может иметь несколько уровней чувствительности к переменам в базовом источнике данных.  
  
 Тип результирующего набора определяется в тот момент, когда создается инструкция, то есть выполняется вызов метода [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Фундаментальная роль результирующего набора заключается в обеспечении приложений Java полезным представлением данных базы данных. Обычно это выполняется посредством введения методов считывания и задания свойств для элементов данных результирующего набора.  
  
 В следующем примере, который основывается на образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], создается результирующий набор посредством вызова метода [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Данные из результирующего набора отображаются при помощи метода [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 В подразделах данного раздела приводится описание различных аспектов использования результирующего набора, включая типы курсора, параллелизм и блокировку строк.  
  
## <a name="in-this-section"></a>в этом разделе  
  
|Раздел|Описание|  
|-----------|-----------------|  
|[Основные сведения о типах курсоров](../../connect/jdbc/understanding-cursor-types.md)|Описывает различные типы курсоров, которые поддерживает драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].|  
|[Общие сведения об управлении параллелизмом](../../connect/jdbc/understanding-concurrency-control.md)|Описывает, как драйвер JDBC поддерживает управление параллелизмом.|  
|[Основные сведения о блокировке строк](../../connect/jdbc/understanding-row-locking.md)|Описывает, как драйвер JDBC поддерживает блокировку строк.|  
  
## <a name="see-also"></a>См. также:  
 [Общие сведения о драйвере JDBC](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

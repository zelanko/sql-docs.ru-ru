---
title: Управление результирующими наборами с помощью драйвера JDBC | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9ed5ad41-22e0-4e4a-8a79-10512db60d50
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 273a03e088036057f6d7b31c98074391138de07e
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/29/2020
ms.locfileid: "69027912"
---
# <a name="managing-result-sets-with-the-jdbc-driver"></a>Управление результирующими наборами с помощью JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Результирующий набор — это объект, представляющий набор данных, которые возвращаются из источника данных, как правило в результате запроса. Результирующий набор содержит строки и столбцы, которые хранят запрошенные элементы данных, переход осуществляется при помощи курсора. Результирующий набор может быть обновлен, то есть его можно изменить, а изменения передать исходному источнику данных. Результирующий набор также может иметь несколько уровней чувствительности к переменам в базовом источнике данных.  
  
 Тип результирующего набора определяется в тот момент, когда создается инструкция, то есть выполняется вызов метода [createStatement](../../connect/jdbc/reference/createstatement-method-sqlserverconnection.md) класса [SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md). Фундаментальная роль результирующего набора заключается в обеспечении приложений Java полезным представлением данных базы данных. Обычно это выполняется посредством введения методов считывания и задания свойств для элементов данных результирующего набора.  
  
 В следующем примере, который основывается на образце базы данных [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)], создается результирующий набор посредством вызова метода [executeQuery](../../connect/jdbc/reference/executequery-method-sqlserverstatement.md) класса [SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md). Данные из результирующего набора отображаются при помощи метода [getString](../../connect/jdbc/reference/getstring-method-sqlserverresultset.md) класса [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
 [!code[JDBC#ManagingResultSets1](../../connect/jdbc/codesnippet/Java/managing-result-sets-with-t_1.java)]  
  
 В подразделах данного раздела приводится описание различных аспектов использования результирующего набора, включая типы курсора, параллелизм и блокировку строк.  
  
## <a name="in-this-section"></a>В этом разделе  
  
|Раздел|Description|  
|-----------|-----------------|  
|[Основные сведения о типах курсоров](../../connect/jdbc/understanding-cursor-types.md)|Описывает различные типы курсоров, которые поддерживает драйвер [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)].|  
|[Основные сведения об управлении параллелизмом](../../connect/jdbc/understanding-concurrency-control.md)|Описывает, как драйвер JDBC поддерживает управление параллелизмом.|  
|[Основные сведения о блокировке строк](../../connect/jdbc/understanding-row-locking.md)|Описывает, как драйвер JDBC поддерживает блокировку строк.|  
  
## <a name="see-also"></a>См. также раздел  
 [Общие сведения о JDBC Driver](../../connect/jdbc/overview-of-the-jdbc-driver.md)  
  
  

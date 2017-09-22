---
title: "JDBC 4.1 соответствия для драйвера JDBC | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f087fd40-8451-478e-b465-43112c711515
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a6aeda8e785fcaabef253a8256b5f6f7a842a324
ms.openlocfilehash: cffe6569f7bac5308d49bb89f4fb4db259be445b
ms.contentlocale: ru-ru
ms.lasthandoff: 09/21/2017

---
# <a name="jdbc-41-compliance-for-the-jdbc-driver"></a>Соответствие JDBC 4.1 для JDBC Driver
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Версии Microsoft JDBC Driver для SQL Server до 4.2 соответствуют спецификациям Java Database Connectivity API 4.0. Этот раздел не применяется к версиям до 4.2.  
  
 Спецификация Java Database Connectivity API 4.1 поддерживается драйвером Microsoft JDBC Driver 4.2 для SQL Server со следующими методами API.  
  
 **Класс SQLServerConnection**  
  
|Новый метод|Description|Реализация драйвера JDBC|  
|----------------|-----------------|--------------------------------|  
|void abort(Executor executor)|Завершает открытое соединение с SQL Server.|Реализовано, как описано в интерфейсе java.sql.Connection. Дополнительные сведения см. в разделе [java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
|void setSchema(String schema)|Задает схему для текущего соединения.|SQL Server не поддерживает установку схемы для текущего сеанса. Драйвер автоматически записывает в журнал предупреждение, если этот метод вызывается. Дополнительные сведения см. в разделе [java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
|String getSchema()|Возвращает имя схемы для текущего соединения.|Поскольку SQL Server не поддерживает установку схемы для текущего соединения, драйвер возвращает пользовательскую схему по умолчанию. Дополнительные сведения см. в разделе [java.sql.Connection](http://docs.oracle.com/javase/7/docs/api/java/sql/Connection.html).|  
  
 **Класс SQLServerDatabaseMetaData**  
  
|Новый метод|Description|Реализация драйвера JDBC|  
|----------------|-----------------|--------------------------------|  
|boolean generatedKeyAlwaysReturned()|Возвращает значение true, если драйвер поддерживает получение созданных ключей.|Реализовано, как описано в java.sql. Интерфейс DatabaseMetaData. Дополнительные сведения см. в разделе [java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html).|  
|ResultSet getPseudoColumns(String catalog, String schemaPattern,String tableNamePattern,String columnNamePattern)|Извлекает описание псевдостолбцов или скрытых столбцов.|Возвращает пустой результирующий набор, так как в SQL Server нет формального понятия псевдостолбцов. Дополнительные сведения см. в разделе [java.sql.DatabaseMetaData](http://docs.oracle.com/javase/7/docs/api/java/sql/DatabaseMetaData.html).|  
  
 **Класс SQLServerStatement**  
  
|Новый метод|Description|Реализация драйвера JDBC|  
|----------------|-----------------|--------------------------------|  
|void closeOnCompletion()|Указывает, что эта инструкция будет закрыта после закрытия всех зависимых результирующих наборов.|Реализовано, как описано в интерфейсе java.sql.Statement. Дополнительные сведения см. в разделе [java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html).|  
|boolean isCloseOnCompletion()|Возвращает значение, указывающее, будет ли эта инструкция закрываться при закрытии всех зависимых результирующих наборов.|Реализовано, как описано в интерфейсе java.sql.Statement. Дополнительные сведения см. в разделе [java.sql.Statement](http://docs.oracle.com/javase/7/docs/api/java/sql/Statement.html).|  
  
 Спецификация Java Database Connectivity API 4.1 поддерживается драйвером Microsoft JDBC 4.2 для SQL Server со следующими возможностями.  
  
|Новая функция|Description|  
|-----------------|-----------------|  
|Новая функция Escape<br /><br /> Ограниченная функция Escape возврата строк|Поддерживается частично<br /><br /> Синтаксис escape-последовательностей: ограничение \<строк > [OFFSET < смещение_строки >](/sql-docs/docs/connect/jdbc/using-sql-escape-sequences).|  
  
 Спецификация Java Database Connectivity API 4.1 поддерживается драйвером Microsoft JDBC 4.2 для SQL Server со следующими сопоставлениями типов данных.  
  
|Сопоставление типов данных|Description|  
|------------------------|-----------------|  
|В методах PreparedStatement.setObject() и PreparedStatement.setNull() теперь поддерживаются новые сопоставления типов данных.|1. Новое сопоставление типов Java с JDBC<br /><br /> (а) java.math.BigInteger с JDBC BIGINT<br /><br /> (б) java.util.Date и java.util.Calendar с JDBC TIMESTAMP<br /><br /> 2. Новые преобразования типов данных:<br /><br /> (а) java.math.BigInteger с CHAR, VARCHAR, LONGVARCHAR и BIGINT<br /><br /> (б) java.util.Date и java.util.Calendar с CHAR, VARCHAR, LONGVARCHAR, DATE, TIME и TIMESTAMP<br /><br /> Дополнительные сведения см. в спецификации JDBC 4.1.|  
  
  

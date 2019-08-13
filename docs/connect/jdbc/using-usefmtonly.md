---
title: Извлечение ParameterMetaData через Усефмтонли | Документация Майкрософт
ms.custom: ''
ms.date: 07/31/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: ''
caps.latest.revision: ''
author: rene-ye
ms.author: v-reye
manager: kenvh
ms.openlocfilehash: 29ee2c5c22baf77b6994a440f1d9d442ba2b812a
ms.sourcegitcommit: a1adc6906ccc0a57d187e1ce35ab7a7a951ebff8
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/09/2019
ms.locfileid: "68894096"
---
# <a name="retrieving-parametermetadata-via-usefmtonly"></a>Получение ParameterMetaData через Усефмтонли
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  Драйвер Microsoft JDBC для SQL Server содержит альтернативный способ запроса метаданных параметров с сервера **усефмтонли**. Эта функция впервые появилась в драйвере версии 7,4 и является обязательной для решения известных проблем в `sp_describe_undeclared_parameters`.
  
  Драйвер в основном использует хранимую процедуру `sp_describe_undeclared_parameters` для запроса метаданных параметров, так как это рекомендуемый подход к получению метаданных параметров в большинстве случаев. Однако выполнение хранимой процедуры в настоящее время завершается ошибкой в следующих случаях:
  
-   Для Always Encrypted столбцов
  
-   Для временных таблиц и табличных переменных
  
-   К представлениям 
  
  Предлагаемое решение для этих вариантов использования — анализ SQL-запроса пользователя для параметров и целевых таблиц, а затем выполнение `SELECT` запроса с `FMTONLY` параметром Enabled. Следующий фрагмент кода поможет визуализировать эту функцию.
  
```sql
--create a normal table 'Foo' and a temporary table 'Bar'
CREATE TABLE Foo(c1 int);
CREATE TABLE #Bar(c1 int);

EXEC sp_describe_undeclared_parameters N'SELECT * FROM Foo WHERE c1 = @p0' --works fine
EXEC sp_describe_undeclared_parameters N'SELECT * FROM #Bar WHERE c1 = @p0' --fails with "Invalid object name '#Bar'"

SET FMTONLY ON;
SELECT c1 FROM Foo; --works
SET FMTONLY OFF;
SET FMTONLY ON;
SELECT c1 FROM #Bar; --works
SET FMTONLY OFF;
```
 
## <a name="turning-the-feature-onoff"></a>Включение или выключение компонента 
 По умолчанию функция **усефмтонли** отключена. Пользователи могут включить эту функцию в строке подключения, указав `useFmtOnly=true`. Например: `jdbc:sqlserver://<server>:<port>;databaseName=<databaseName>;user=<user>;password=<password>;useFmtOnly=true;`.
 
 Кроме того, эта функция доступна через `SQLServerDataSource`.
 ```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName(<server>);
ds.setPortNumber(<port>);
ds.setDatabaseName("<databaseName>");
ds.setUser("<user>");
ds.setPassword("<password>");
ds.setUseFmtOnly(true);
try (Connection c = ds.getConnection()) {
    // do work with connection
}
 ```
 
 Эта функция также доступна на уровне инструкций. Пользователи могут включать и выключать эту функцию `PreparedStatement.setUseFmtOnly(boolean)`с помощью.
> [!NOTE]  
>  Драйвер будет определять приоритет свойства уровня инструкции для свойства уровня соединения.

## <a name="using-the-feature"></a>Использование функции
  После включения драйвер будет внутренним образом начать использовать новую функцию, а не `sp_describe_undeclared_parameters` при запросе метаданных параметров. От конечного пользователя не требуется предпринимать никаких действий.
```java
final String sql = "INSERT INTO #Bar VALUES (?)";
try (Connection c = DriverManager.getConnection(URL, USERNAME, PASSWORD)) {
    try (Statement s = c.createStatement()) {
        s.execute("CREATE TABLE #Bar(c1 int)");
    }
    try (PreparedStatement p1 = c.prepareStatement(sql); PreparedStatement p2 = c.prepareStatement(sql)) {
        ((SQLServerPreparedStatement) p1).setUseFmtOnly(true);
        ParameterMetaData pmd1 = p1.getParameterMetaData();
        System.out.println(pmd1.getParameterTypeName(1)); // prints int
        ParameterMetaData pmd2 = p2.getParameterMetaData(); // throws exception, Invalid object name '#Bar'
    }
}
```
> [!NOTE]  
>  Эта функция поддерживает `SELECT/INSERT/UPDATE/DELETE` только запросы. Запросы должны начинаться с одного из 4 поддерживаемых ключевых слов или [обобщенного табличного выражения](https://docs.microsoft.com/sql/t-sql/queries/with-common-table-expression-transact-sql?view=sql-server-2017) , за которым следует один из поддерживаемых запросов. Параметры в обобщенных табличных выражениях не поддерживаются.

## <a name="known-issues"></a>Известные проблемы
  С этой функцией сейчас связаны некоторые проблемы из-за недостатков в логике синтаксического анализа SQL. Эти проблемы могут быть решены в будущем обновлении функции, и они описаны ниже вместе с предложениями по решению проблемы.
  
A. Использование псевдонима "Forwarded"
```sql
CREATE TABLE Foo(c1 int)

DELETE fooAlias FROM Foo fooAlias WHERE c1 > ?; --Invalid object name 'fooAlias'

--Workaround #1: Specify AS keyword
DELETE fooAlias FROM Foo AS fooAlias WHERE c1 > ?;
--Workaround #2: Use the table name
DELETE Foo FROM Foo fooAlias WHERE c1 > ?;
```

Б. Неоднозначное имя столбца, если у таблиц есть имена общих столбцов
```sql
CREATE TABLE Foo(c1 int, c2 int, c3 int)
CREATE TABLE Bar(c1 int, c2 int, c3 int)

SELECT c1,c2 FROM Foo WHERE c3 IN (SELECT c3 FROM Bar WHERE c1 > ? and c2 < ? and c3 = ?); --Ambiguous Column Name

--Workaround: Use aliases
SELECT c1,c2 FROM Foo WHERE c3 IN (SELECT c3 FROM Bar b WHERE b.c1 = ? and b.c2 = ? and b.c3 = ?);
```

В. ВЫБОР из вложенного запроса с параметрами
```sql

CREATE TABLE Foo(c1 int)

SELECT * FROM (SELECT * FROM Foo WHERE c1 = ?) WHERE c1 = ?; --Incorrect syntax near '?'

--Workaround: N/A
```

Г. Вложенные запросы в предложении SET
```sql
CREATE TABLE Foo(c1 int)

UPDATE Foo SET c1 = (SELECT c1 FROM Foo) WHERE c1 = ?; --Incorrect syntax near ')'

--Workaround: Add a 'delimiting' condition
UPDATE Foo SET c1 = (SELECT c1 FROM Foo HAVING (HASH JOIN)) WHERE c1 = ?;
```

## <a name="see-also"></a>См. также раздел  
 [Задание свойств соединения](../../connect/jdbc/setting-the-connection-properties.md)  
  
  

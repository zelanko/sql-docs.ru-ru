---
title: Обработка ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6277b3ecf0160078fa47bc79994d31f64519d9b7
ms.sourcegitcommit: 9348f79efbff8a6e88209bb5720bd016b2806346
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 08/14/2019
ms.locfileid: "69028029"
---
# <a name="handling-errors"></a>Обработка ошибок
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] все ошибки базы данных возвращаются в приложение Java в виде исключений через класс [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Приведенные далее методы класса SQLServerException унаследованы от классов java.sql.SQLException и java.lang.Throwable. Их можно использовать для возвращения специфической информации о возникшей ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   `getSQLState()` возвращает стандартный код состояния исключения X/Open или SQL99.
  
-   `getErrorCode()` возвращает специфический номер ошибки базы данных.
  
-   `getMessage()` возвращает полный текст исключения. В тексте сообщения об ошибке описывается проблема и зачастую содержатся заполнители для информации, такие как имена объектов, которые вставляются в сообщение об ошибке во время отображения.
  
-   `getNextException()` возвращает следующий объект `SQLServerException` или значение NULL, если нет других объектов исключений для возвращения.

-   `getSQLServerError()`Возвращает объект `SQLServerError` , содержащий подробные сведения об исключении, полученные от SQL Server. Этот метод возвращает значение null, если ошибка сервера не возникла.

Следующие методы `SQLServerError` класса можно использовать для получения дополнительных сведений об ошибке, созданной на сервере.

-   `SQLServerError.getErrorMessage()`Возвращает сообщение об ошибке, полученное от сервера.

-   `SQLServerError.getErrorNumber()`Возвращает число, определяющее тип ошибки.

-   `SQLServerError.getErrorState()`Возвращает числовой код ошибки из SQL Server, который представляет сообщение об ошибке, предупреждении или "не найдено данных".

-   `SQLServerError.getErrorSeverity()`Возвращает степень серьезности полученной ошибки.

-   `SQLServerError.getServerName()`Возвращает имя компьютера, на котором работает экземпляр SQL Server, вызвавший ошибку.

-   `SQLServerError.getProcedureName()`Возвращает имя хранимой процедуры или удаленного вызова процедуры (RPC), вызвавшего ошибку.

-   `SQLServerError.getLineNumber()`Возвращает номер строки в пакете команд Transact-SQL или хранимой процедуре, вызвавшей ошибку.
  
 В следующем примере открытое соединение с образцом базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию и создается инструкция SQL неправильного формата, которая не имеет предложения FROM. Далее инструкция выполняется и происходит обработка исключения SQL.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>См. также раздел  
 [Диагностика проблем с JDBC Driver](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  

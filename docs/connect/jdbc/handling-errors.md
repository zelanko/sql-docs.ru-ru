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
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/31/2020
ms.locfileid: "69028029"
---
# <a name="handling-errors"></a>Обработка ошибок
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] все ошибки базы данных возвращаются в приложение Java в виде исключений через класс [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Приведенные далее методы класса SQLServerException унаследованы от классов java.sql.SQLException и java.lang.Throwable. Их можно использовать для возвращения специфической информации о возникшей ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   `getSQLState()` возвращает стандартный код состояния исключения X/Open или SQL99.
  
-   `getErrorCode()` возвращает специфический номер ошибки базы данных.
  
-   `getMessage()` возвращает полный текст исключения. В тексте сообщения об ошибке описывается проблема и зачастую содержатся заполнители для информации, такие как имена объектов, которые вставляются в сообщение об ошибке во время отображения.
  
-   `getNextException()` возвращает следующий объект `SQLServerException` или значение NULL, если нет других объектов исключений для возвращения.

-   `getSQLServerError()` возвращает объект `SQLServerError` с подробными сведениями об исключении, полученными от SQL Server. Если ошибок не было, этот метод возвращает значение NULL.

Следующие методы класса `SQLServerError` можно применить для получения дополнительных сведений об ошибке, созданной на сервере.

-   `SQLServerError.getErrorMessage()` возвращает сообщение об ошибке, которое вернул сервер.

-   `SQLServerError.getErrorNumber()` возвращает номер, который обозначает тип ошибки.

-   `SQLServerError.getErrorState()` возвращает числовой код ошибки, полученный из SQL Server, который обозначает ошибку, предупреждение или сообщение "данные не найдены".

-   `SQLServerError.getErrorSeverity()` возвращает уровень серьезности полученной ошибки.

-   `SQLServerError.getServerName()` возвращает имя компьютера, на котором работает создавший ошибку экземпляр SQL Server.

-   `SQLServerError.getProcedureName()` возвращает имя хранимой процедуры или удаленного вызова процедуры, в которой произошла ошибка.

-   `SQLServerError.getLineNumber()` возвращает номер строки в пакете команд Transact-SQL или хранимой процедуре, в которой произошла ошибка.
  
 В следующем примере открытое соединение с образцом базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию и создается инструкция SQL неправильного формата, которая не имеет предложения FROM. Далее инструкция выполняется и происходит обработка исключения SQL.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>См. также раздел  
 [Диагностика проблем с JDBC Driver](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  

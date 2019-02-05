---
title: Обработка ошибок | Документация Майкрософт
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8fd5b5ef-d939-4b78-b900-5b7b6ddb3eb9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 535881ed3ece30996390af6c9a22568d49bc6d3e
ms.sourcegitcommit: 879a5c6eca99e0e9cc946c653d4ced165905d9c6
ms.translationtype: MTE75
ms.contentlocale: ru-RU
ms.lasthandoff: 02/05/2019
ms.locfileid: "55736973"
---
# <a name="handling-errors"></a>Обработка ошибок
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  При использовании [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] все ошибки базы данных возвращаются в приложение Java в виде исключений через класс [SQLServerException](../../connect/jdbc/reference/sqlserverexception-class.md). Приведенные далее методы класса SQLServerException унаследованы от классов java.sql.SQLException и java.lang.Throwable. Их можно использовать для возвращения специфической информации о возникшей ошибке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   `getSQLState()` возвращает стандартный код состояния исключения X/Open или SQL99.
  
-   `getErrorCode()` возвращает специфический номер ошибки базы данных.
  
-   `getMessage()` возвращает полный текст исключения. В тексте сообщения об ошибке описывается проблема и зачастую содержатся заполнители для информации, такие как имена объектов, которые вставляются в сообщение об ошибке во время отображения.
  
-   `getNextException()` возвращает следующий объект `SQLServerException` или значение NULL, если нет других объектов исключений для возвращения.

-   `getSQLServerError()` Возвращает `SQLServerError` объект, содержащий подробные сведения об исключении как полученный из SQL Server. Этот метод возвращает значение null, если ошибка не сервера.

Следующие методы класса `SQLServerError` класс может использоваться для получения дополнительных сведений об ошибке, созданные на сервере.

-   `SQLServerError.getErrorMessage()` Возвращает сообщение об ошибке, как полученный от сервера.

-   `SQLServerError.getErrorNumber()` Возвращает число, определяющее тип ошибки.

-   `SQLServerError.getErrorState()` Возвращает числовой код ошибки из SQL Server, который представляет ошибку, предупреждение или сообщение «не удалось найти данные».

-   `SQLServerError.getErrorSeverity()` Возвращает степень серьезности сообщение об ошибке.

-   `SQLServerError.getServerName()` Возвращает имя компьютера, на котором выполняется экземпляр SQL Server, на котором создается ошибка.

-   `SQLServerError.getProcedureName()` Возвращает имя хранимой процедуры или удаленного вызова процедур (RPC), выдавшего ошибку.

-   `SQLServerError.getLineNumber()` Возвращает номер строки в пакете команд Transact-SQL или хранимой процедуры, вызвавшей ошибку.
  
 В следующем примере открытое соединение с образцом базы данных [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)] передается в функцию и создается инструкция SQL неправильного формата, которая не имеет предложения FROM. Далее инструкция выполняется и происходит обработка исключения SQL.  
  
 [!code[JDBC#HandlingErrors1](../../connect/jdbc/codesnippet/Java/handling-errors_1.java)]  
  
## <a name="see-also"></a>См. также:  
 [Диагностика проблем с драйвером JDBC](../../connect/jdbc/diagnosing-problems-with-the-jdbc-driver.md)  
  
  

---
title: Использование операторов утверждений Transact-SQL в модульных тестах SQL Server | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: 55d8be9c-9282-47d3-be7f-e2c26f00c95e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 8da09c20837b060606b087c0edebb7bf9713675e
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51671252"
---
# <a name="using-transact-sql-assertions-in-sql-server-unit-tests"></a>Использование проверочных утверждений Transact-SQL в модульных тестах SQL Server
При выполнении модульного теста SQL Server запускается тестовый скрипт Transact\-SQL и возвращается его результат. Иногда результаты возвращаются в виде результирующего набора. Результаты можно проверить с помощью условий теста. Например, по тестовому условию можно проверить число возвращенных строк в результирующем наборе. Можно также проверить время, которое заняло выполнение конкретного теста. Дополнительные сведения об условиях теста см. в статье [Использование условий теста в модульных тестах SQL Server](../ssdt/using-test-conditions-in-sql-server-unit-tests.md).  
  
Вместо условий теста можно воспользоваться утверждениями Transact\-SQL, которые определяются с помощью инструкций THROW или RAISERROR в скрипте Transact\-SQL. В определенных обстоятельствах утверждения Transact\-SQL будут более предпочтительны, чем условия теста.  
  
## <a name="using-transact-sql-assertions"></a>Использование проверочных утверждений Transact-SQL  
Прежде чем принимать решение о проверке данных через утверждения Transact\-SQL или через условия теста, следует учесть следующие моменты.  
  
-   **Производительность**. Быстрее выполнить утверждение Transact\-SQL на сервере, чем передавать данные на клиентский компьютер и обрабатывать их локально.  
  
-   **Степень владения языком**. Возможно, опыт владения языками будет для вас важным фактором при выборе между утверждениями Transact\-SQL, условиями теста Visual C\# и Visual Basic.  
  
-   **Сложная проверка.** В некоторых случаях можно создать более сложные тесты на Visual C\# или Visual Basic и выполнять проверку этих тестов в клиенте.  
  
-   **Простота**. Часто проще использовать предопределенные условия теста, чем писать аналогичные скрипты на Transact\-SQL.  
  
-   **Старые библиотеки проверки**. Если у вас есть уже код для выполнения проверки, его можно использовать в модульном тесте SQL Server вместо условий теста.  
  
## <a name="mark-unit-test-methods-with-the-expected-exception"></a>Пометка методов модульного теста ожидаемым исключением  
Чтобы отметить в методе модульного теста SQL Server ожидаемые исключения, добавьте следующий атрибут:  
  
```vb  
<ExpectedSqlException(MessageNumber=nnnnn, Severity=x, MatchFirstError=false, State=y)> _  
```  
  
```csharp  
[ExpectedSqlException(MessageNumber=nnnnn, Severity=x, MatchFirstError=false, State=y)]  
```  
  
Где:  
  
-   *nnnnn* — номер ожидаемого сообщения, например 14025;  
  
-   *x* — серьезность ожидаемого исключения;  
  
-   *y* — состояние ожидаемого исключения.  
  
Любые неуказанные параметры не используются. Эти параметры передаются инструкции RAISERROR в коде базы данных. Если указано MatchFirstError = true, то атрибут будет в исключении соответствовать любой из SqlErrors. По умолчанию (MatchFirstError = true) сопоставление происходит только с первой возникшей ошибкой.  
  
Пример использования ожидаемых исключений и отрицательного модульного теста SQL Server см. в статье [Пошаговое руководство. Создание и запуск модульного теста SQL Server](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md).  
  
## <a name="the-raiserror-statement"></a>Инструкция RAISERROR  
  
> [!NOTE]  
> Используйте THROW вместо RAISERROR. Предложение RAISERROR является устаревшим.  
  
Утверждения Transact\-SQL можно выполнять непосредственно на сервере, добавив инструкцию RAISERROR в скрипт Transact\-SQL. Синтаксис:  
  
**RAISERROR (@ErrorMessage, @ErrorSeverity, @ErrorState)**  
  
где:  
  
@ErrorMessage — это любое сообщение об ошибке. Форматирование строки сообщения производится так же, как и в функции printf_s.  
  
@ErrorSeverity — определяемая пользователем степень серьезности в диапазоне от 0 до 18.  
  
> [!NOTE]  
> Значения степени серьезности 0 и 10 не приводят к сбою модульного теста SQL Server. Чтобы вызвать сбой проверки, необходимо указывать значение в диапазоне от 0 до 18.  
  
@ErrorState — произвольное целое число в диапазоне от 1 до 127. Оно служит для различения повторений одной и той же ошибки, возникшей в разных местах кода.  
  
Дополнительные сведения см. в разделе справки [RAISERROR (Transact-SQL)](https://msdn.microsoft.com/library/ms178592.aspx). Пример использования RAISERROR в модульном тесте SQL Server приведен в статье [Практическое руководство. Написание модульного теста SQL Server, который выполняется в области действия одной транзакции](../ssdt/how-to-write-sql-server-unit-test-that-runs-in-single-transaction-scope.md).  
  
## <a name="see-also"></a>См. также:  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[Использование условий теста в модульных тестах SQL Server](../ssdt/using-test-conditions-in-sql-server-unit-tests.md)  
[Проверка кода базы данных с помощью модульных тестов SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
[Практическое руководство. Открытие модульного теста SQL Server для изменения](../ssdt/how-to-open-a-sql-server-unit-test-to-edit.md)  
  

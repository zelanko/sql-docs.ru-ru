---
title: Выполнение модульных тестов SQL Server | Документация Майкрософт
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.unittesting.testconfig
ms.assetid: febcc87f-eb18-4c12-ba30-82ef0d49aaa3
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35ed4fd4090a3a7ef5cff862817bbaec592749a3
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/15/2018
ms.locfileid: "51670683"
---
# <a name="running-sql-server-unit-tests"></a>Выполнение модульных тестов SQL Server
Для поддержания и улучшения качества кода создаются и выполняются модульные тесты SQL Server, которые позволяют проверить объект базы данных. Затем такие тесты заносятся в систему управления версиями. Если схема базы данных изменяется, необходимо запустить модульные тесты SQL Server и программного обеспечения, чтобы убедиться, что изменения не повлияли на существующую функциональность. Можно выполнять как отдельные тесты, так и группы тестов, которые также называют списками тестов. Дополнительные сведения см. в статье [Использование списков тестов](https://msdn.microsoft.com/library/ms182461(VS.100).aspx) для Visual Studio 2010.  
  
## <a name="ways-to-run-sql-server-unit-tests"></a>Способы запуска модульных тестов SQL Server  
Модульные тесты SQL Server можно запускать несколькими способами в зависимости от установленного программного обеспечения (см. сведения ниже).  
  
-   Выполнение тестов с помощью окна Visual Studio 2010 **Представление теста**. Дополнительные сведения см. в практических руководствах по [выполнению модульных тестов SQL Server](../ssdt/how-to-run-sql-server-unit-tests.md) и [запуску автоматических тестов из Microsoft Visual Studio 2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx). Для Visual Studio 2012 процесс описан в статье [Практическое руководство. Запуск тестов из Microsoft Visual Studio](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Запуск тестов при помощи команды MSTest.exe из командной строки. Дополнительные сведения см. в практических руководствах по запуску автоматических тестов из командной строки с помощью MSTest для Visual Studio [2010](https://msdn.microsoft.com/library/ms182487(VS.100).aspx) и [2012](https://msdn.microsoft.com/library/ms182487.aspx).  
  
-   Запуск тестов из **обозревателя решений** путем запуска тестового проекта. Дополнительные сведения см. в практических руководствах по запуску автоматических тестов из командной строки с помощью MSTest для Visual Studio [2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx) и [2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Повторный запуск тестов из окна **Результаты теста**. Дополнительные сведения см. в статье [Практическое руководство. Повторное выполнение теста](https://msdn.microsoft.com/library/ms182472(VS.100).aspx).  
  
-   Запуск отдельных тестов или списков тестов (Visual Studio 2010) из окна **редактора списка тестов**. Дополнительные сведения см. в практических руководствах по запуску автоматических тестов из командной строки с помощью MSTest для Visual Studio [2010](https://msdn.microsoft.com/library/ms182470(VS.100).aspx) и [2012](https://msdn.microsoft.com/library/ms182470.aspx).  
  
-   Запуск тестов при построении проекта в среде Team Foundation Build. Дополнительные сведения см. в практических руководствах по настройке и запуску запланированных тестов после создания приложения для Visual Studio[2010](https://msdn.microsoft.com/library/ms182465(VS.100).aspx) и [2012](https://msdn.microsoft.com/library/ms182465.aspx).  
  
Модульные тесты SQL Server можно запускать в определенном порядке при помощи упорядоченного теста. Дополнительные сведения о создании упорядоченных тестов см. в [этой статье для Visual Studio 2010](https://msdn.microsoft.com/library/ms182631(VS.100).aspx) или в [этой статье для Visual Studio 2012](https://msdn.microsoft.com/library/ms182631.aspx).  
  
## <a name="interpreting-tests-results"></a>Интерпретация результатов тестов  
После выполнения тестов в окне **Результаты тестов** будет показано, какие тесты были успешно выполнены, а какие завершились ошибкой. Дополнительные сведения см. в статье [Интерпретация результатов модульного теста SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md). Дополнительные сведения о диагностике непредвиденных ошибок см. в статье [Практическое руководство. Отладка объектов базы данных](../ssdt/how-to-debug-database-objects.md).  
  
## <a name="topics-in-this-section"></a>Подразделы в этом разделе  
В этом разделе рассматриваются следующие вопросы.  
  
-   [Практическое руководство. Отладка объектов базы данных](../ssdt/how-to-debug-database-objects.md)  
  
-   [How to: Run SQL Server Unit Tests from Team Foundation Build](../ssdt/how-to-run-sql-server-unit-tests-from-team-foundation-build.md) (Практическое руководство. Запуск модульных тестов SQL Server из сборки Team Foundation)  
  
-   [Практическое руководство. Выполнение модульных тестов SQL Server](../ssdt/how-to-run-sql-server-unit-tests.md)  
  
-   [Интерпретация результатов модульного теста SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md)  
  
## <a name="related-scenarios"></a>Связанные сценарии  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
Для проверки поведения объектов базы данных и связывания каждого тестового проекта со своим планом формирования данных, конфигурацией развертывания и строкой подключения используются разные модульные тесты.  
  
[Пользовательские условия теста для модульных тестов SQL Server](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
Для тестирования условий, которые нельзя проверить с помощью тестовых условий по умолчанию, следует использовать пользовательские тестовые условия.  
  
## <a name="see-also"></a>См. также:  
[Проверка кода базы данных с помощью модульных тестов SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  

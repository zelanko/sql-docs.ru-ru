---
title: Выполнение модульных тестов SQL Server
description: Ознакомьтесь с модульными тестами в SQL Server. Просмотрите ресурсы по созданию тестов, созданию пользовательских условий тестов, выполнению тестов и интерпретации результатов.
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- sql.data.tools.unittesting.testconfig
ms.assetid: febcc87f-eb18-4c12-ba30-82ef0d49aaa3
author: markingmyname
ms.author: maghan
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 810010b70a50f51c29b34b917af90127233d622c
ms.sourcegitcommit: a41e1f4199785a2b8019a419a1f3dcdc15571044
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/13/2020
ms.locfileid: "91987800"
---
# <a name="running-sql-server-unit-tests"></a>Выполнение модульных тестов SQL Server

Для поддержания и улучшения качества кода создаются и выполняются модульные тесты SQL Server, которые позволяют проверить объект базы данных. Затем такие тесты заносятся в систему управления версиями. Если схема базы данных изменяется, необходимо запустить модульные тесты SQL Server и программного обеспечения, чтобы убедиться, что изменения не повлияли на существующую функциональность. Можно выполнять как отдельные тесты, так и группы тестов, которые также называют списками тестов. Дополнительные сведения см. в статье [Использование списков тестов](/previous-versions/visualstudio/visual-studio-2010/ms182461(v=vs.100)) для Visual Studio 2010.  
  
## <a name="ways-to-run-sql-server-unit-tests"></a>Способы запуска модульных тестов SQL Server  
Модульные тесты SQL Server можно запускать несколькими способами в зависимости от установленного программного обеспечения (см. сведения ниже).  
  
-   Выполнение тестов с помощью окна Visual Studio 2010 **Представление теста**. Дополнительные сведения см. в разделе [Как запускать модульные тесты SQL Server](../ssdt/how-to-run-sql-server-unit-tests.md) и [Как запускать автоматические тесты из Microsoft Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/ms182470(v=vs.100)). Для Visual Studio 2012 см. раздел [Как запускать автоматические тесты из Microsoft Visual Studio 2012](/previous-versions/ms182470(v=vs.140)).  
  
-   Запуск тестов при помощи команды MSTest.exe из командной строки. Дополнительные сведения см. в практических руководствах по запуску автоматических тестов из командной строки с помощью MSTest для Visual Studio [2010](/previous-versions/visualstudio/visual-studio-2010/ms182487(v=vs.100)) и [2012](/previous-versions/ms182487(v=vs.140)).  
  
-   Запуск тестов из **обозревателя решений** путем запуска тестового проекта. Дополнительные сведения см. в практических руководствах по запуску автоматических тестов из командной строки с помощью MSTest для Visual Studio [2010](/previous-versions/visualstudio/visual-studio-2010/ms182470(v=vs.100)) и [2012](/previous-versions/ms182470(v=vs.140)).  
  
-   Повторный запуск тестов из окна **Результаты теста**. Дополнительные сведения см. в разделе [Как повторно запустить тест (Visual Studio 2010)](/previous-versions/visualstudio/visual-studio-2010/ms182472(v=vs.100)).  
  
-   Запуск отдельных тестов или списков тестов (Visual Studio 2010) из окна **редактора списка тестов**. Дополнительные сведения см. в практических руководствах по запуску автоматических тестов из командной строки с помощью MSTest для Visual Studio [2010](/previous-versions/visualstudio/visual-studio-2010/ms182470(v=vs.100)) и [2012](/previous-versions/ms182470(v=vs.140)).  
  
-   Запуск тестов при построении проекта в среде Team Foundation Build. Дополнительные сведения см. в практических руководствах по настройке и запуску запланированных тестов после создания приложения для Visual Studio[2010](/previous-versions/visualstudio/visual-studio-2010/ms182465(v=vs.100)) и [2012](/previous-versions/visualstudio/visual-studio-2012/ms182465(v=vs.110)).  
  
Модульные тесты SQL Server можно запускать в определенном порядке при помощи упорядоченного теста. Дополнительные сведения см. в разделе [Как создавать упорядоченные тесты (Visual Studio 2010)](/previous-versions/visualstudio/visual-studio-2010/ms182631(v=vs.100)) или [Как создавать упорядоченные тесты (Visual Studio 2012)](/previous-versions/ms182631(v=vs.140)).  
  
## <a name="interpreting-tests-results"></a>Интерпретация результатов тестов  
После выполнения тестов в окне **Результаты тестов** будет показано, какие тесты были успешно выполнены, а какие завершились ошибкой. Дополнительные сведения см. в статье [Интерпретация результатов модульного теста SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md). Дополнительные сведения о диагностике непредвиденных ошибок см. в разделе [Как выполнить отладку объектов базы данных](../ssdt/how-to-debug-database-objects.md).  
  
## <a name="topics-in-this-section"></a>Подразделы в этом разделе  
В этом разделе рассматриваются следующие вопросы.  
  
-   [Руководство. выполнить отладку объектов базы данных](../ssdt/how-to-debug-database-objects.md)  
  
-   [Руководство. выполнить модульные тесты SQL Server из сборки Team Foundation](../ssdt/how-to-run-sql-server-unit-tests-from-team-foundation-build.md)  
  
-   [Руководство. выполнять модульные тесты SQL Server](../ssdt/how-to-run-sql-server-unit-tests.md)  
  
-   [Интерпретация результатов модульного теста SQL Server](../ssdt/interpreting-sql-server-unit-test-results.md)  
  
## <a name="related-scenarios"></a>Связанные сценарии  
[Создание и определение модульных тестов SQL Server](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
Для проверки поведения объектов базы данных и связывания каждого тестового проекта со своим планом формирования данных, конфигурацией развертывания и строкой подключения используются разные модульные тесты.  
  
[Пользовательские условия теста для модульных тестов SQL Server](../ssdt/custom-test-conditions-for-sql-server-unit-tests.md)  
Для тестирования условий, которые нельзя проверить с помощью тестовых условий по умолчанию, следует использовать пользовательские тестовые условия.  
  
## <a name="see-also"></a>См. также:  
[Проверка кода базы данных с помощью модульных тестов SQL Server](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  

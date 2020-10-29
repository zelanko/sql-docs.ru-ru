---
title: Что представляет собой расширение языка Java?
description: В SQL Server 2019 поддерживаются расширение языков Java, R и Python. Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода.  Реляционные данные могут использоваться во внешнем коде с помощью платформы расширяемости.
author: cawrites
ms.author: chadam
ms.date: 10/06/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: f6b7f2c21aa79ee5c0c9657cf817d9801b5d2891
ms.sourcegitcommit: 2b6760408de3b99193edeccce4b92a2f9ed5bcc6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2020
ms.locfileid: "92175902"
---
# <a name="what-is-java-language-extension"></a>Что представляет собой расширение языка Java?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода. Реляционные данные могут использоваться во внешнем коде с помощью [платформы расширяемости](concepts/extensibility-framework.md).

В SQL Server 2019 поддерживается язык Java. Среда выполнения Java по умолчанию — Zulu Open JRE. Можно также использовать другую среду Java JRE или пакет SDK.

> [!NOTE]
> Сведения о запуске Python или R в SQL Server см. в документации по [машинному обучению SQL](../machine-learning/index.yml). В SQL Server 2019 и более поздних версий можно использовать настраиваемые среды выполнения Python и R с расширениями языка. Дополнительные сведения см. в разделе [Настраиваемая среда выполнения Python](../machine-learning/install/custom-runtime-python.md) и [Настраиваемая среда выполнения R](../machine-learning/install/custom-runtime-r.md).

## <a name="what-you-can-do-with-language-extensions"></a>Возможности расширений языка

Расширения языка используют платформу расширяемости для исполнения внешнего кода. Выполнение кода изолировано от процессов ядра, но полностью интегрировано с выполнением запросов SQL Server. Вы можете выполнять код в источнике данных, чтобы не передавать данные по сети.

Внешние языки определяются с помощью инструкции [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql). Системная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) используется в качестве интерфейса для исполнения кода.

Использование расширений языка обеспечивает различные преимущества:

+ Защита данных. Выполнение кода внешнего языка ближе к источнику данных позволяет избежать затратного и небезопасного перемещения данных.
+ Скорость. Базы данных оптимизированы для операций на основе наборов. Последние нововведения в базах данных, такие как таблицы в памяти, делают выполнение сводок и агрегатов молниеносным и являются идеальным дополнением к обработке и анализу данных.
+ Простота развертывания и интеграции. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] является отправной точкой операций для многих других задач и приложений управления данными. Извлекая данные из базы данных, вы гарантируете, что в Java используются согласованные и актуальные данные.

## <a name="how-to-get-started"></a>Начало работы

### <a name="step-1-install-the-software"></a>Шаг 1. Установите программное обеспечение

+ [Расширения языка для SQL Server в Windows](install/windows-java.md)
+ [Расширения языка для SQL Server в Linux](../linux/sql-server-linux-setup-language-extensions-java.md)

### <a name="step-2-configure-a-development-tool"></a>Шаг 2. Настройте среду разработки

Разработчики обычно пишут код на своем ноутбуке или на рабочей станции для разработки. При использовании расширений языка в SQL Server нет необходимости изменять этот процесс. После завершения установки можно запустить код Java на SQL Server.

+ **Используйте свою привычную интегрированную среду разработки** для написания кода Java.

+ **Установите [Пакет Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md)** для выполнения кода Java на SQL Server

+ **Используйте [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) или [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)** для исполнения внешнего кода в SQL Server

+ **Используйте системную хранимую процедуру [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)** для выполнения кода Java на SQL Server.

### <a name="step-3-write-your-first-code"></a>Шаг 3. Напишите свой первый код

Выполните код Java в сценарии T-SQL:

+ [Руководство. Регулярные выражения с Java](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>Ограничения

+ Количество значений в буферах ввода и вывода не может превышать значение `MAX_INT (2^31-1)`, так как это максимальное количество элементов, которое может быть выделено для массива в Java.

## <a name="next-steps"></a>Дальнейшие действия

+ Установка [настраиваемой среды выполнения Python для SQL Server](../machine-learning/install/custom-runtime-python.md)
+ Установка [настраиваемой среды выполнения R для SQL Server](../machine-learning/install/custom-runtime-r.md)
+ Установка [Расширений языка для SQL Server в Windows](../language-extensions/install/windows-java.md) или [в Linux](../linux/sql-server-linux-setup-language-extensions-java.md)
+ Установка [Пакета Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md)

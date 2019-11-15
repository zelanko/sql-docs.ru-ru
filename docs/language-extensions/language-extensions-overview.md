---
title: Что такое расширения языка для SQL Server?
titleSuffix: ''
description: Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода. В SQL Server 2019 поддерживается язык Java. Реляционные данные могут использоваться во внешнем коде с помощью платформы расширяемости.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 57755782f2907eff25db942600cebc63f09598e0
ms.sourcegitcommit: baa40306cada09e480b4c5ddb44ee8524307a2ab
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/06/2019
ms.locfileid: "73658820"
---
# <a name="what-is-sql-server-language-extensions"></a>Что такое расширения языка для SQL Server?
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода. Реляционные данные могут использоваться во внешнем коде с помощью [платформы расширяемости](concepts/extensibility-framework.md).

В SQL Server 2019 поддерживается язык Java. Среда выполнения Java по умолчанию — Zulu Open JRE. Можно также использовать другую среду Java JRE или пакет SDK.

## <a name="what-you-can-do-with-language-extensions"></a>Возможности расширений языка

Расширения языка используют платформу расширяемости для исполнения внешнего кода. Выполнение кода изолировано от процессов ядра, но полностью интегрировано с выполнением запросов SQL Server. Расширения языка позволяют выполнять код там, где находятся данные, устраняя необходимость извлечения данных по сети.

Внешние языки определяются с помощью инструкции [CREATE EXTERNAL LANGUAGE](https://docs.microsoft.com/sql/t-sql/statements/create-external-language-transact-sql). Системная хранимая процедура [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql) используется в качестве интерфейса для исполнения кода.

Использование расширений языка имеет несколько преимуществ.

+ Защита данных. Выполнение кода внешнего языка ближе к источнику данных позволяет избежать затратного и небезопасного перемещения данных.
+ Скорость. Базы данных оптимизированы для операций на основе наборов. Последние нововведения в базах данных, такие как таблицы в памяти, делают выполнение сводок и агрегатов молниеносным и являются идеальным дополнением к обработке и анализу данных.
+ Простота развертывания и интеграции. [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] является отправной точкой операций для многих других задач и приложений управления данными. Извлекая данные непосредственно из базы данных, вы гарантируете, что в Java используются согласованные и актуальные данные.

## <a name="how-to-get-started"></a>Начало работы

### <a name="step-1-install-the-software"></a>Шаг 1. Установите программное обеспечение

+ [Расширения языка для SQL Server в Windows](install/install-sql-server-language-extensions-on-windows.md)
+ [Расширения языка для SQL Server в Linux](../linux/sql-server-linux-setup-language-extensions.md)

### <a name="step-2-configure-a-development-tool"></a>Шаг 2. Настройте среду разработки

Разработчики обычно пишут код на своем ноутбуке или на рабочей станции для разработки. При использовании расширений языка в SQL Server нет необходимости изменять этот процесс. После завершения установки можно запустить код Java на SQL Server.

+ **Используйте свою привычную интегрированную среду разработки** для написания кода Java.

+ **Установите [Пакет Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md)** для выполнения кода Java на SQL Server

+ **Используйте [Azure Data Studio](https://docs.microsoft.com/sql/azure-data-studio/what-is) или [SQL Server Management Studio](https://docs.microsoft.com/sql/ssms/sql-server-management-studio-ssms)** для исполнения внешнего кода в SQL Server

+ **Используйте системную хранимую процедуру [sp_execute_external_script](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql)** для выполнения кода Java на SQL Server.

### <a name="step-3-write-your-first-code"></a>Шаг 3. Напишите свой первый код

Выполните код Java в сценарии T-SQL:

+ [Учебник. Регулярные выражения с Java](tutorials/search-for-string-using-regular-expressions-in-java.md)

## <a name="limitations"></a>Ограничения

+ Количество значений в буферах ввода и вывода не может превышать значение `MAX_INT (2^31-1)`, так как это максимальное количество элементов, которое может быть выделено для массива в Java.

## <a name="next-steps"></a>Дальнейшие действия

+ Установка [Расширений языка для SQL Server в Windows](install/install-sql-server-language-extensions-on-windows.md) или [в Linux](../linux/sql-server-linux-setup-language-extensions.md)
+ Установка [Пакета Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md)

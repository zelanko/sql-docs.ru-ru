---
title: Что такое расширения языка для SQL Server?
titleSuffix: ''
description: Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода. В SQL Server 2019 поддерживаются Java, R и Python. Реляционные данные могут использоваться во внешнем коде с помощью платформы расширяемости.
author: dphansen
ms.author: davidph
ms.date: 10/07/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: c4482adb86f9a2f205bd64044a18f342cf3e13c5
ms.sourcegitcommit: 43b92518c5848489d03c68505bd9905f8686cbc0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92154949"
---
# <a name="what-is-sql-server-language-extensions"></a>Что такое расширения языка для SQL Server?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода. Реляционные данные могут использоваться во внешнем коде с помощью [платформы расширяемости](concepts/extensibility-framework.md).

В SQL Server 2019 поддерживаются Java, R и Python.

> [!NOTE]
> Сведения о запуске Python или R в SQL Server см. в документации по [машинному обучению SQL](../machine-learning/index.yml). В SQL Server 2019 и более поздних версий можно использовать настраиваемые среды выполнения Python и R с расширениями языка. Дополнительные сведения см. в разделе [Настраиваемая среда выполнения Python](../machine-learning/install/custom-runtime-python.md) и [Настраиваемая среда выполнения R](../machine-learning/install/custom-runtime-r.md).

## <a name="what-you-can-do-with-language-extensions"></a>Возможности расширений языка

Расширения языка используют платформу расширяемости для исполнения внешнего кода. Выполнение кода изолировано от процессов ядра, но полностью интегрировано с выполнением запросов SQL Server. Вы можете выполнять код в источнике данных, чтобы не передавать данные по сети.

Внешние языки определяются с помощью инструкции [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). Системная хранимая процедура [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) используется в качестве интерфейса для исполнения кода.

Использование расширений языка имеет несколько преимуществ.

+ Защита данных. Выполнение кода внешнего языка ближе к источнику данных позволяет избежать затратного и небезопасного перемещения данных.
+ Скорость. Базы данных оптимизированы для операций на основе наборов. Последние нововведения в базах данных, такие как таблицы в памяти, делают выполнение сводок и агрегатов молниеносным и являются идеальным дополнением к обработке и анализу данных.
+ Простота развертывания и интеграции. [!INCLUDE [ssNoVersion](../includes/ssnoversion-md.md)] является отправной точкой операций для многих других задач и приложений управления данными. Используя данные в базе данных, вы гарантируете, что языковое расширение использует согласованные и актуальные данные.

## <a name="next-steps"></a>Дальнейшие действия

+ Установка [настраиваемой среды выполнения Python для SQL Server](../machine-learning/install/custom-runtime-python.md)
+ Установка [настраиваемой среды выполнения R для SQL Server](../machine-learning/install/custom-runtime-r.md)
+ Установка [Расширений языка для SQL Server в Windows](install/windows-java.md) или [в Linux](../linux/sql-server-linux-setup-language-extensions-java.md)
+ Установка [Пакета Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md)

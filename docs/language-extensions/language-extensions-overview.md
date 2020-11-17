---
title: Что такое расширения языка для SQL Server?
titleSuffix: ''
description: Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода. В SQL Server поддерживаются Java, R и Python. Реляционные данные могут использоваться во внешнем коде с помощью платформы расширяемости.
author: dphansen
ms.author: davidph
ms.date: 11/06/2020
ms.topic: overview
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e62b61e2b90f3a2f3ec837115d99a65070571c57
ms.sourcegitcommit: 06cb1751b1bc7420dbe4ad4555ab1afc5fc5bd71
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/07/2020
ms.locfileid: "94361755"
---
# <a name="what-is-sql-server-language-extensions"></a>Что такое расширения языка для SQL Server?
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Расширения языка — это функция SQL Server, используемая для выполнения внешнего кода. Реляционные данные могут использоваться во внешнем коде с помощью [платформы расширяемости](concepts/extensibility-framework.md). В SQL Server 2019 поддерживаются среды выполнения Java, R и Python.

> [!NOTE]
> Сведения о запуске Python или R в SQL Server см. в документации по [Службам машинного обучения](../machine-learning/sql-server-machine-learning-services.md). В SQL Server 2019 и более поздних версий можно использовать настраиваемые среды выполнения Python и R с расширениями языка. Дополнительные сведения см. в статье [Установка настраиваемой среды выполнения Python для SQL Server](../machine-learning/install/custom-runtime-python.md) и [Установка настраиваемой среды выполнения R для SQL Server](../machine-learning/install/custom-runtime-r.md).

## <a name="what-you-can-do-with-language-extensions"></a>Возможности расширений языка

Расширения языка используют [платформу расширяемости](concepts/extensibility-framework.md) для исполнения внешнего кода. Выполнение кода изолировано от процессов ядра, но полностью интегрировано с выполнением запросов SQL Server. Вы можете выполнять код в источнике данных, чтобы не передавать данные по сети.

Внешние языки определяются с помощью инструкции [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md). Системная хранимая процедура [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) используется в качестве интерфейса для исполнения кода.

Использование расширений языка имеет несколько преимуществ.

+ Защита данных. Выполнение кода внешнего языка ближе к источнику данных позволяет избежать небезопасного перемещения данных.
+ Скорость. Базы данных оптимизированы для операций на основе наборов. 
+ Простота развертывания и интеграции. [!INCLUDE [ssNoVersion](../includes/ssnoversion-md.md)] является отправной точкой операций для многих других задач и приложений управления данными. Используя данные в базе данных, вы гарантируете, что языковое расширение использует согласованные и актуальные данные.

## <a name="next-steps"></a>Дальнейшие действия

+ Установка [Расширений языка для SQL Server в Windows](install/windows-java.md) или [в Linux](../linux/sql-server-linux-setup-language-extensions-java.md)
+ Установка [настраиваемой среды выполнения Python для SQL Server](../machine-learning/install/custom-runtime-python.md)
+ Установка [настраиваемой среды выполнения R для SQL Server](../machine-learning/install/custom-runtime-r.md)
+ Установка [Пакета Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md)

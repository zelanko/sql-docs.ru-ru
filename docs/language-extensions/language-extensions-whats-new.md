---
title: Новые возможности расширений языка SQL Server
titleSuffix: ''
description: Узнайте о новых возможностях языковых расширений для SQL Server, которые улучшают, расширяют и укрепляют интеграцию между внешними языками и платформой данных.
author: dphansen
ms.author: davidph
ms.date: 11/05/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: language-extensions
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 1583ab8c54d16d7bcf129e401c2e540fabb342b3
ms.sourcegitcommit: 43b92518c5848489d03c68505bd9905f8686cbc0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/17/2020
ms.locfileid: "92155095"
---
# <a name="whats-new-in-sql-server-language-extensions"></a>Новые возможности расширений языка SQL Server
[!INCLUDE [SQL Server 2019 and later](../includes/applies-to-version/sqlserver2019.md)]

Возможности [расширений языка](language-extensions-overview.md) добавляются в SQL Server в каждом выпуске, так как мы продолжаем расширять и углублять интеграцию между внешними языками и платформой данных.

## <a name="new-python-and-r-language-extensions-in-sql-server-2019"></a>Новые расширения языков Python и R в SQL Server 2019

+ Для [Python в Windows](../machine-learning/install/custom-runtime-python.md) доступна настраиваемая среда выполнения. Об установке на Linux см. статью [Установка настраиваемой среды выполнения Python для SQL Server на Linux](../machine-learning/install/custom-runtime-python.md?view=sql-server-linux-ver15&preserve-view=true).

+ Для [R в Windows](../machine-learning/install/custom-runtime-r.md) доступна настраиваемая среда выполнения. Об установке на Linux см. статью [Установка настраиваемую среды выполнения R для SQL Server на Linux](../machine-learning/install/custom-runtime-r.md?view=sql-server-linux-ver15&preserve-view=true)


## <a name="new-java-language-extension-in-sql-server-2019"></a>Новое расширение языка Java в SQL Server 2019

Дополнительные сведения обо всех возможностях этого выпуска см. в статьях [Новые возможности SQL Server 2019](../sql-server/what-s-new-in-sql-server-ver15.md) и [Заметки о выпуске SQL Server 2019](../sql-server/sql-server-version-15-release-notes.md).

- Средой выполнения Java по умолчанию в Windows и Linux является Open Zulu JRE и входит в состав [установки расширений языка SQL Server для Windows ](install/windows-java.md) и [установки расширений языка SQL Server для Linux](../linux/sql-server-linux-setup-language-extensions-java.md).
- Поддержка [типов данных Java](how-to/java-to-sql-data-types.md).
- Инструкция [CREATE EXTERNAL LANGUAGE](../t-sql/statements/create-external-language-transact-sql.md) для регистрации внешнего языка (например, Java) в SQL Server.
- [Пакет Microsoft Extensibility SDK для Java](how-to/extensibility-sdk-java-sql-server.md).
- В Windows и Linux доступ к коду Java можно получить во внешней библиотеке с помощью инструкции [CREATE EXTERNAL LIBRARY (Transact-SQL)](../t-sql/statements/create-external-library-transact-sql.md). Дополнительные сведения: [Вызов кода Java из SQL Server](how-to/call-java-from-sql.md).
- [Расширение языка Java](language-extensions-overview.md) в Windows и Linux. Можно сделать скомпилированный код Java доступным в SQL Server путем назначения разрешений и установки пути. Клиентские приложения с доступом SQL Server могут использовать данные и выполнять код, вызывая [sp_execute_external_script](../relational-databases/system-stored-procedures/sp-execute-external-script-transact-sql.md) — ту же самую процедуру, которая используется для интеграции языков R и Python в службы машинного обучения SQL Server.

## <a name="next-steps"></a>Дальнейшие действия

+ Установка [расширений языка для SQL Server в Windows](install/windows-java.md) или [в Linux](../linux/sql-server-linux-setup-language-extensions-java.md)
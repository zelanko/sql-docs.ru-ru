---
title: Предварительные требования для данного пошагового руководства обработки и анализа данных для SQL Server и R | Документы Microsoft
ms.date: 11/10/2017
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: c8f3c74bb38ea358de0342126038b51e4404657b
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/04/2018
---
# <a name="prerequisites-for-the-data-science-walkthrough-for-sql-server-and-r"></a>Предварительные требования для данного пошагового руководства обработки и анализа данных для SQL Server и R
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

Мы рекомендуем сделать в этом пошаговом руководстве на ноутбук или другой компьютер с Microsoft R библиотеки, установленные. Необходимо подключиться, в одной сети с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера с компьютера службы обучения и языка R включены.

Пошаговое руководство можно запустить на компьютере, на котором содержатся оба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и среду разработки R, но мы не рекомендуем этой конфигурации для рабочей среды.

## <a name="install-machine-learning-for-sql-server"></a>Установка машинного обучения для SQL Server

Необходимо иметь доступ к экземпляру SQL Server с поддержкой R установлен. В этом пошаговом руководстве был первоначально, разработанные для SQL erver 2016 и протестировано для 2017 г., поэтому можно использовать любой из следующих версий SQL Server. (Отсутствуют некоторые небольшие различия в функциях RevoScaleR между версиями).

+ Машинного обучения службы (в базе данных) для SQL Server 2017 г.
+ SQL Server 2016 R Services

Дополнительные сведения см. в разделе [установки служб SQL Server 2017 г машины обучения](../install/sql-machine-learning-services-windows-install.md) или [установки служб SQL Server 2016 R](../install/sql-r-services-windows-install.md).

> [!IMPORTANT]
> Версии SQL Server более ранней версии 2016 не поддерживают интеграцию с R. Однако старых баз данных SQL можно использовать как источник данных ODBC.

## <a name="install-an-r-development-environment"></a>Установите среду разработки R

В этом пошаговом руководстве рекомендуется использовать среду разработки R. Ниже приведены некоторые рекомендации.

- **Средства R для Visual Studio** (RTVS) — это бесплатная подключаемый модуль, который предоставляет Intellisense, отладки и поддержку R. Вы можно использовать с R Server и служб SQL Server машины обучения. Чтобы скачать эти средства, перейдите на страницу [Средства R для Visual Studio](https://www.visualstudio.com/vs/rtvs/).

- **Клиент Microsoft R** — это средство разработки, которое поддерживает разработку на языке R, с помощью пакета RevoScaleR. Чтобы получить его, см. статью о [начале работы с клиентом Microsoft R](https://docs.microsoft.com/machine-learning-server/r-client/what-is-microsoft-r-client).

- **RStudio** — одна из наиболее популярных сред для разработки на языке R. Дополнительные сведения см. в разделе [ https://www.rstudio.com/products/RStudio/ ](https://www.rstudio.com/products/RStudio/).

    Не удается завершить этот учебник, с помощью универсального установки RStudio или в другой среде; R-пакетов и библиотек подключений, необходимо также установить для Microsoft R Open. Дополнительные сведения см. в разделе [Настройка клиента обработки и анализа данных](../r/set-up-a-data-science-client.md).

- Основные средства R (R.exe RTerm.exe, RScripts.exe) также устанавливаются по умолчанию при установке R в SQL Server или R клиента. Если вы не хотите установить интегрированной среды разработки, можно использовать эти инструменты.

## <a name="get-permissions-on-the-sql-server-instance-and-database"></a>Получение разрешений на экземпляр SQL Server и базы данных

Для подключения к экземпляру компонента [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] для запуска скриптов и передачи данных, необходимо иметь допустимое имя входа на сервере базы данных.  Можно использовать либо имя входа SQL, либо встроенную проверку подлинности Windows. Попросите администратора базы данных, настройте следующие разрешения для учетной записи в базе данных, где используется R:

- создание базы данных, таблиц, функций и хранимых процедур;
- Запись данных в таблицы
- Возможность выполнения скрипта R (`GRANT EXECUTE ANY EXTERNAL SCRIPT to <user>`)

В данном пошаговом руководстве мы использовали имя входа SQL **RTestUser**. Мы рекомендуем использовать встроенную проверку подлинности Windows, что имя входа SQL с помощью проще некоторые в целях демонстрации.

## <a name="change-list"></a>Список изменений

+ В этом примере было разработано с использованием служб R SQL Server 2016. Тем не менее критические изменения появились в компонентах Microsoft R 2016 SP1. В частности _varsToDrop_ и _varsToKeep_ параметры больше не поддерживались для источников данных SQL Server. Therefre, если вы загрузили версии учебника до SP1, он будет больше не работать со сборками post SP1.

+ Текущая версия образца были проверены с помощью предварительной версии сборки служб SQL Server 2017 г машины обучения (RC1 и версии-кандидата 2). Как правило почти все действия должны выполняться без изменения между 2016 SP1 и 2017 г.

## <a name="next-lesson"></a>Следующее занятие

[Подготовка данных с помощью PowerShell](/walkthrough-prepare-the-data.md)

---
title: "Предварительные требования для данного пошагового руководства обработки и анализа данных для SQL Server и R | Документы Microsoft"
ms.custom:
- SQL2016_New_Updated
ms.date: 08/23/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
ms.assetid: 0b0582b8-8843-4787-94a8-2e28bdc04fb2
caps.latest.revision: 13
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: b9d3a579f023a7e6d9805b934edc3f0e9e5ad5e8
ms.contentlocale: ru-ru
ms.lasthandoff: 09/01/2017

---
# <a name="prerequisites-for-the-data-science-walkthrough-for-sql-server-and-r"></a>Предварительные требования для данного пошагового руководства обработки и анализа данных для SQL Server и R

Мы рекомендуем сделать в этом пошаговом руководстве на ноутбук или другой компьютер с Microsoft R библиотеки, установленные. Необходимо подключиться, в одной сети с [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] компьютера с компьютера службы обучения и языка R включены.

Пошаговое руководство можно запустить на компьютере, на котором содержатся оба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и среду разработки R, но мы не рекомендуем этой конфигурации для рабочей среды.

## <a name="install-machine-learning-for-sql-server"></a>Установка машинного обучения для SQL Server

Необходимо иметь доступ к экземпляру SQL Server с поддержкой R установлен, с помощью любого из следующих:

+ Машинного обучения службы (в базе данных) для SQL Server 2017 г.
+ SQL Server 2016 R Services

Дополнительные сведения см. в разделе [настроить SQL Server R Services (в базе данных](../r/set-up-sql-server-r-services-in-database.md).

> [!IMPORTANT]
> Обязательно используйте [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] или более поздней версии. Предыдущие версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] не поддерживают интеграцию с R, но вы можете использовать предыдущие версии баз данных SQL в качестве источника данных ODBC.

## <a name="install-an-r-development-environment"></a>Установите среду разработки R

В этом пошаговом руководстве рекомендуется использовать среду разработки R. Ниже приведены некоторые рекомендации.

- **Средства R для Visual Studio** (RTVS) — это бесплатная подключаемый модуль, который предоставляет Intellisense, отладки и поддержку R. Вы можно использовать с R Server и служб SQL Server машины обучения. Чтобы скачать эти средства, перейдите на страницу [Средства R для Visual Studio](https://www.visualstudio.com/features/rtvs-vs.aspx).

- **Клиент Microsoft R** — это упрощенное средство разработки, которое поддерживает разработку на языке R с использованием пакетов ScaleR. Чтобы получить его, см. статью о [начале работы с клиентом Microsoft R](https://msdn.microsoft.com/microsoft-r/r-client-get-started).

- **RStudio** — одна из наиболее популярных сред для разработки на языке R. Дополнительные сведения см. на странице [https://www.rstudio.com/products/RStudio/](https://www.rstudio.com/products/RStudio/).

    Не удается завершить этот учебник, с помощью универсального установки RStudio или в другой среде; R-пакетов и библиотек подключений, необходимо также установить для Microsoft R Open. Дополнительные сведения см. в разделе [Настройка клиента обработки и анализа данных](../r/set-up-a-data-science-client.md).

- Основные средства R (R.exe RTerm.exe, RScripts.exe) также устанавливаются по умолчанию при установке [!INCLUDE[rsql_rro-noversion](../../includes/rsql-rro-noversion-md.md)]. Если вы не хотите установить интегрированной среды разработки, можно использовать эти инструменты.

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


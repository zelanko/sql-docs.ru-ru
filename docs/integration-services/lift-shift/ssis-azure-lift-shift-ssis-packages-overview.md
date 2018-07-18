---
title: Развертывание и выполнение пакетов служб SSIS в Azure | Документы Майкрософт
description: Узнайте, как перенести проекты, пакеты и рабочие нагрузки служб SQL Server Integration Services (SSIS) в облако Microsoft Azure.
ms.date: 06/07/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.suite: sql
ms.custom: ''
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 0fa7a72e86f596cd0e5d18a0c0dbeb1015233f20
ms.sourcegitcommit: cc46afa12e890edbc1733febeec87438d6051bf9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/12/2018
ms.locfileid: "35403296"
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Перенос рабочих нагрузок SQL Server Integration Services в облако
Проекты, пакеты и рабочие нагрузки служб SQL Server Integration Services (SSIS) теперь можно переносить в облако Azure.
-   Храните проекты и пакеты служб SSIS и управляйте ими в каталоге SSIS (SSISDB), размещенном в базе данных SQL Azure или в управляемом экземпляре базы данных SQL (предварительная версия).
-   Запускайте пакеты в экземпляре Azure-SSIS Integration Runtime, компоненте фабрики данных Azure.
-   Используйте привычные вам инструменты, такие как SQL Server Management Studio (SSMS), для решения типичных задач.

## <a name="benefits"></a>Преимущества
Перенос локальных рабочих нагрузок служб SSIS в Azure имеет следующие потенциальные преимущества:
-   **Сокращение операционных затрат** и усилий на управление инфраструктурой, которые требуются, когда службы SSIS выполняются локально или в виртуальных машинах Azure.
-   **Повышение уровня доступности** благодаря возможности указывать несколько узлов в каждом кластере, а также использовать функции обеспечения высокой доступности Azure и базы данных SQL Azure.
-   **Повышение масштабируемости** благодаря возможности указывать несколько ядер на узел (вертикальное масштабирование) и несколько узлов на кластер (горизонтальное масштабирование).

## <a name="architecture-overview"></a>Обзор архитектуры
В приведенной ниже таблице представлены различия между локальными службами SSIS и службами SSIS в Azure. Главное различие заключается в разделении хранилища и среды выполнения. В фабрике данных Azure размещается подсистема среды выполнения для пакетов SSIS в Azure. Подсистема среды выполнения называется Azure-SSIS Integration Runtime (Azure-SSIS IR). Дополнительные сведения: [Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime).

| Память | Параметры выполнения | Масштабируемость |
|---|---|---|
| Локальная среда (SQL Server) | Среда выполнения служб SSIS размещается в SQL Server | SSIS Scale Out (в SQL Server 2017 и более поздних версиях)<br/><br/>Пользовательские решения (в предыдущих версиях SQL Server) |
| В Azure (база данных SQL или управляемый экземпляр базы данных SQL (предварительная версия)) | Azure-SSIS Integration Runtime, компонент фабрики данных Azure | Параметры масштабирования для Azure-SSIS Integration Runtime |
| | | |

Azure-SSIS IR достаточно подготовить только один раз. После этого можно использовать знакомые средства, такие как SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS) для развертывания, настройки, запуска, мониторинга, планирования пакетов и управления ими.

## <a name="version-support"></a>Поддерживаемые версии

В Azure можно развертывать пакеты, создаваемые в любых версиях SSIS. Если при развертывании пакета в Azure отсутствуют ошибки проверки, формат пакета автоматически обновляется до последней версии. Другими словами, пакет будет всегда обновлен до последней версии SSIS.

В процессе развертывания проверяется возможность выполнения пакета в среде Azure-SSIS Integration Runtime. Дополнительные сведения см. в статье [Проверка пакетов SSIS, развертываемых в Azure](ssis-azure-validate-packages.md).

## <a name="prerequisites"></a>предварительные требования

Для развертывания пакетов SSIS в Azure нужна одна из следующих версий SQL Server Data Tools (SSDT):
-   Для Visual Studio 2017 — 15.3 или более поздняя версия.
-   для Visual Studio 2015 версия 17.2 или более поздняя.

Сведения о необходимых компонентах Azure-SSIS Integration Runtime см. в статье [Развертывание и выполнение пакета служб SSIS — предварительные требования](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure#prerequisites).

> [!NOTE]
> На этапе общедоступной предварительной версии среда Azure-SSIS Integration Runtime доступна не во всех регионах. Сведения о поддерживаемых регионах см. на странице [Доступность продуктов по регионам — Microsoft Azure](https://azure.microsoft.com/regions/services/).

## <a name="provision-ssis-on-azure"></a>Подготовка служб SSIS к работе в Azure

**Подготовка**. Перед тем как развертывать и выполнять пакеты SSIS в Azure, необходимо подготовить каталог SSIS (SSISDB) и среду Azure-SSIS Integration Runtime. Следуйте инструкциям по подготовке в этой статье: [Развертывание и запуск пакета служб SSIS в Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

**Вертикальное и горизонтальное масштабирование**. При подготовке среды Azure-SSIS IR вы можете осуществлять вертикальное и горизонтальное масштабирование, указывая значения для следующих параметров:
-   размер узла (включая число ядер) и число узлов в кластере;
-   существующий экземпляр базы данных SQL Azure для размещения базы данных каталога SSIS (SSISDB) и уровень обслуживания базы данных;
-   максимальное число параллельных выполнений в каждом узле.

**Повышение производительности**. Дополнительные сведения см. в статье [Настройка высокого уровня производительности в Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/configure-azure-ssis-integration-runtime-performance).

## <a name="design-packages"></a>Проектирование пакетов

Вы можете продолжать **проектировать и создавать пакеты** в локальной среде в средствах SSDT или в Visual Studio с установленными средствами SSDT.

### <a name="connect-to-data-sources"></a>Подключение к источникам данных

Сведения о подключении к локальным источникам данных из облака с использованием **проверки подлинности Windows** см. в статье [Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows](ssis-azure-connect-with-windows-auth.md).

Сведения о подключении к файлам и общим папкам см. в статье [Открытие и сохранение файлов с помощью пакетов SSIS, развернутых в Azure](ssis-azure-files-file-shares.md).

### <a name="available-ssis-components"></a>Доступные компоненты SSIS

При подготовке экземпляра базы данных SQL для размещения базы данных SSISDB также устанавливаются пакет дополнительных компонентов Azure для служб SSIS и распространяемый компонент Access. Эти компоненты обеспечивают подключение к различным источникам данных **Azure**, файлам **Excel и Access**, а также источникам данных, поддерживаемым встроенными компонентами.

Можно также установить дополнительные компоненты. Например, можно установить драйвер, который не устанавливается по умолчанию. Дополнительные сведения см. в разделе [Выборочная установка среды выполнения интеграции Azure-SSIS](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

Если вы независимый поставщик программного обеспечения, вы можете обновить установку лицензированных компонентов, чтобы сделать их доступными в Azure. Дополнительные сведения: [Разработка платных или лицензируемых пользовательских компонентов для Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/how-to-develop-azure-ssis-ir-licensed-components).

### <a name="transaction-support"></a>Поддержка транзакций

При использовании локальных виртуальных машин SQL Server и виртуальных машин Azure вы можете применять транзакции из координатора распределенных транзакций (Майкрософт) — MSDTC. Чтобы настроить MSDTC на каждом узле Azure-SSIS Integration Runtime, используйте функцию пользовательской настройки. Дополнительные сведения см. в разделе [Выборочная установка среды выполнения интеграции Azure-SSIS](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

При использовании базы данных SQL Azure вы можете применять только эластичные транзакции. Дополнительные сведения: [Распределенные транзакции в облачных базах данных](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-transactions-overview).

## <a name="deploy-and-run-packages"></a>Развертывание и запуск пакетов

Сначала ознакомьтесь со статьей [Развертывание и запуск пакета служб SSIS в Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="connect-to-ssisdb"></a>Подключение к SSISDB

**Имя базы данных SQL**, в которой размещается база данных SSISDB, станет первой частью четырехкомпонентного имени, которое применяется при развертывании и запуске пакетов из SSDT и SSMS в следующем формате: `<sql_database_name>.database.windows.net`. Сведения о подключении к базе данных каталога SSIS в Azure см. в статье [Подключение к каталогу SSIS (SSISDB) в Azure](ssis-azure-connect-to-catalog-database.md).

### <a name="deploy-projects-and-packages"></a>Развертывание проектов и пакетов

Для проектов, развертываемых в базе данных SSISDB в Azure, необходимо использовать **модель развертывания проектов**, а не модель развертывания пакетов.

Для развертывания проектов в Azure можно использовать одно из знакомых средств и скриптов:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (в SSMS, Visual Studio Code или другом средстве)
-   Программа командной строки
-   PowerShell или C# и объектная модель управления служб SSIS

Пример развертывания с использованием служб SSMS и мастера развертывания служб Integration Services см. в статье [Развертывание и запуск пакета служб SSIS в Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="run-packages"></a>Выполнение пакетов

Обзор методов, которые можно использовать для запуска пакетов служб SSIS, развернутых в Azure, см. в статье [Выполнение пакета служб SSIS в Azure](ssis-azure-run-packages.md).

## <a name="pass-runtime-values-with-environments"></a>Передача значений времени выполнения с помощью сред

Чтобы передать одно значение времени выполнения или несколько в пакеты, запускаемые в составе конвейера фабрики данных Azure, создайте среды выполнения служб SSIS в SSISDB с помощью SQL Server Management Studio (SSMS). В каждой среде создайте переменные и присвойте значения, которые соответствуют параметрам для проектов или пакетов. Настройте пакеты служб SSIS в среде SSMS, чтобы связать эти переменные среды с параметрами проекта или пакета. Если пакеты выполняются в конвейере фабрики данных, переключайтесь между средами, указывая пути к разным средам на вкладке "Параметры" пользовательского интерфейса действия "Выполнение пакета служб SSIS".

Дополнительные сведения о средах SSIS см. в статье [Создание и сопоставление серверной среды](../packages/deploy-integration-services-ssis-projects-and-packages.md#create-and-map-a-server-environment). Сведения о выполнении пакета в составе конвейера фабрики данных Azure см. в статье [Выполнение пакета служб SSIS с помощью действия "Выполнение пакета служб SSIS" в фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

## <a name="monitor-packages"></a>Мониторинг пакетов
Для отслеживания запускаемых пакетов в SSMS вы можете использовать следующие аналитические средства.
-   Щелкните базу данных **SSISDB** правой кнопкой мыши и выберите пункт **Активные операции**, чтобы открыть диалоговое окно **Активные операции**.
-   Выберите пакет в обозревателе объектов, щелкните его правой кнопкой мыши, выберите пункт **Отчеты**, затем — **Стандартные отчеты** и **Все выполнения**.

Сведения о мониторинге Azure-SSIS Integration Runtime: [Мониторинг Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime).

## <a name="schedule-packages"></a>Планирование выполнения пакетов
Запланировать запуск пакетов, хранящихся в базе данных SQL Azure, можно разными средствами. Дополнительные сведения см. в разделе [Планирование выполнения пакетов служб SSIS в Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Следующие шаги
Чтобы приступить к работе с рабочими нагрузками служб SSIS в Azure, ознакомьтесь со следующими статьями:
-   [Развертывание пакетов SQL Server Integration Services в Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Развертывание и запуск пакета служб SSIS в Azure](ssis-azure-deploy-run-monitor-tutorial.md)

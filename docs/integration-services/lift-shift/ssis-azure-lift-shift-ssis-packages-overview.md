---
title: Развертывание и выполнение пакетов служб SSIS в Azure | Документы Майкрософт
description: Узнайте, как перенести проекты, пакеты и рабочие нагрузки служб SQL Server Integration Services (SSIS) в облако Microsoft Azure.
ms.date: 09/23/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
ms.openlocfilehash: 0a402c50e8a7f1c2467b00fbbaa599d6c289ebab
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67896182"
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Перенос рабочих нагрузок SQL Server Integration Services в облако

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


Проекты, пакеты и рабочие нагрузки служб SQL Server Integration Services (SSIS) теперь можно переносить в облако Azure. Для управления, развертывания и выполнения проектов и пакетов SSI и в каталоге SSI (SSISDB), размещенном в службе "База данных SQL Azure" или Управляемом экземпляре базы данных SQL, вы можете использовать привычные вам инструменты, например SQL Server Management Studio (SSMS).

## <a name="benefits"></a>Преимущества
Перенос локальных рабочих нагрузок служб SSIS в Azure имеет следующие потенциальные преимущества:
-   **Сокращение операционных затрат** и усилий на управление инфраструктурой, которые требуются, когда службы SSIS выполняются локально или в виртуальных машинах Azure.
-   **Повышение уровня доступности** благодаря возможности указывать несколько узлов в каждом кластере, а также использовать функции обеспечения высокой доступности Azure и базы данных SQL Azure.
-   **Повышение масштабируемости** благодаря возможности указывать несколько ядер на узел (вертикальное масштабирование) и несколько узлов на кластер (горизонтальное масштабирование).

## <a name="architecture-of-ssis-on-azure"></a>Архитектура MSSQL Integration Services в Azure
В приведенной ниже таблице представлены различия между локальными службами SSIS и службами SSIS в Azure.

Главное различие заключается в разделении хранилища и среды выполнения. В фабрике данных Azure размещается подсистема среды выполнения для пакетов SSIS в Azure. Подсистема среды выполнения называется Azure-SSIS Integration Runtime (Azure-SSIS IR). Дополнительные сведения: [Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/concepts-integration-runtime#azure-ssis-integration-runtime).

| Местоположение | Память | Параметры выполнения | Масштабируемость |
|---|---|---|---|
| В локальной среде | SQL Server | Среда выполнения служб SSIS размещается в SQL Server | SSIS Scale Out (в SQL Server 2017 и более поздних версиях)<br/><br/>Пользовательские решения (в предыдущих версиях SQL Server) |
| В Azure | Служба "База данных SQL" или Управляемый экземпляр базы данных SQL | Azure-SSIS Integration Runtime, компонент фабрики данных Azure | Параметры масштабирования для Azure-SSIS Integration Runtime |
| | | | |

## <a name="provision-ssis-on-azure"></a>Подготовка служб SSIS к работе в Azure

**Подготовка**. Перед тем как развертывать и выполнять пакеты SSIS в Azure, необходимо подготовить каталог SSIS (SSISDB) и среду Azure-SSIS Integration Runtime.

-   Чтобы подготовить SSIS в Azure на портале Azure, выполните инструкции из этой статьи: [Подготовка Azure-SSIS Integration Runtime в Фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure). 

-   Чтобы подготовить SSIS в Azure с помощью PowerShell, выполните инструкции из этой статьи: [Подготовка Azure-SSIS Integration Runtime в Фабрике данных Azure с помощью PowerShell](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure-powershell).

Azure-SSIS IR достаточно подготовить только один раз. После этого можно использовать знакомые средства, такие как SQL Server Data Tools (SSDT) и SQL Server Management Studio (SSMS) для развертывания, настройки, запуска, мониторинга, планирования пакетов и управления ими.

> [!NOTE]
> Среда Integration Runtime Azure — SSI доступна пока не во всех регионах Azure. Сведения о поддерживаемых регионах см. на странице [Доступность продуктов по регионам — Microsoft Azure](https://azure.microsoft.com/regions/services/).

**Вертикальное и горизонтальное масштабирование**. При подготовке среды Azure-SSIS IR вы можете осуществлять вертикальное и горизонтальное масштабирование, указывая значения для следующих параметров:
-   размер узла (включая число ядер) и число узлов в кластере;
-   существующий экземпляр базы данных SQL Azure для размещения базы данных каталога SSIS (SSISDB) и уровень обслуживания базы данных;
-   максимальное число параллельных выполнений в каждом узле.

**Повышение производительности**. Дополнительные сведения см. в статье [Настройка высокого уровня производительности в Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/configure-azure-ssis-integration-runtime-performance).

**Сокращение затрат**. Чтобы снизить затраты, запускайте среду Integration Services Azure — SSI только тогда, когда она нужна. См. дополнительные сведения о [запуске и остановке среды выполнения интеграции Azure – SSI по расписанию](https://docs.microsoft.com/azure/data-factory/how-to-schedule-azure-ssis-integration-runtime).

## <a name="design-packages"></a>Проектирование пакетов

Вы можете продолжать **проектировать и создавать пакеты** в локальной среде в средствах SSDT или в Visual Studio с установленными средствами SSDT.

### <a name="connect-to-data-sources"></a>Подключение к источникам данных

Чтобы подключиться к локальным источникам данных из облака с использованием **проверки подлинности Windows**, см. статьей [Подключение к источникам данных и общим папкам с помощью проверки подлинности Windows в пакетах SQL Server Integration Services в Azure](ssis-azure-connect-with-windows-auth.md).

Сведения о подключении к файлам и общим папкам см. в статье [Открытие и сохранение файлов в локальной среде и в Azure с помощью пакетов SSI, развернутых в Azure](ssis-azure-files-file-shares.md).

### <a name="available-ssis-components"></a>Доступные компоненты SSIS

При подготовке экземпляра базы данных SQL для размещения базы данных SSISDB также устанавливаются пакет дополнительных компонентов Azure для служб SSIS и распространяемый компонент Access. Эти компоненты обеспечивают подключение к различным источникам данных **Azure**, файлам **Excel и Access**, а также источникам данных, поддерживаемым встроенными компонентами.

Можно также установить дополнительные компоненты. Например, можно установить драйвер, который не устанавливается по умолчанию. Дополнительные сведения см. в статье [Customize setup for the Azure-SSIS integration runtime](/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup) (Настройка установки для среды выполнения интеграции Azure — SSIS).

Владельцам лицензия Enterprise Edition доступны дополнительные компоненты. Дополнительные сведения см. в статье [Подготовка выпуска Enterprise Edition для среды выполнения интеграции Azure Integration Services](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-enterprise-edition).

Если вы независимый поставщик программного обеспечения, вы можете обновить установку лицензированных компонентов, чтобы сделать их доступными в Azure. Дополнительные сведения: [Установка платных или лицензионных пользовательских компонентов для среды выполнения интеграции Azure – SSI](https://docs.microsoft.com/azure/data-factory/how-to-develop-azure-ssis-ir-licensed-components).

### <a name="transaction-support"></a>Поддержка транзакций

При использовании локальных виртуальных машин SQL Server и виртуальных машин Azure вы можете применять транзакции из координатора распределенных транзакций (Майкрософт) — MSDTC. Чтобы настроить MSDTC на каждом узле Azure-SSIS Integration Runtime, используйте функцию пользовательской настройки. Дополнительные сведения см. в разделе [Выборочная установка среды выполнения интеграции Azure-SSIS](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

При использовании базы данных SQL Azure вы можете применять только эластичные транзакции. Дополнительные сведения: [Распределенные транзакции в облачных базах данных](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-transactions-overview).

## <a name="deploy-and-run-packages"></a>Развертывание и запуск пакетов

Чтобы быстро приступить к работе, см. руководство по [ развертыванию и запуску пакета служб SQL Server Integration Services (SSI) в Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="prerequisites"></a>предварительные требования

Для развертывания пакетов SSIS в Azure нужна одна из следующих версий SQL Server Data Tools (SSDT):
-   Для Visual Studio 2017 — 15.3 или более поздняя версия.
-   для Visual Studio 2015 версия 17.2 или более поздняя.

### <a name="connect-to-ssisdb"></a>Подключение к SSISDB

**Имя базы данных SQL**, в которой размещается база данных SSISDB, станет первой частью четырехкомпонентного имени, которое применяется при развертывании и запуске пакетов из SSDT и SSMS в следующем формате: `<sql_database_name>.database.windows.net`. См. дополнительные сведения о [подключении к базе данных каталога SSI (SSISDB) в Azure](ssis-azure-connect-to-catalog-database.md).

### <a name="deploy-projects-and-packages"></a>Развертывание проектов и пакетов

Для проектов, развертываемых в базе данных SSISDB в Azure, необходимо использовать **модель развертывания проектов**, а не модель развертывания пакетов.

Для развертывания проектов в Azure можно использовать одно из знакомых средств и скриптов:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (в SSMS, Visual Studio Code или другом средстве)
-   Программа командной строки
-   PowerShell или C# и объектная модель управления служб SSIS

В процессе развертывания проверяется возможность выполнения пакета в среде Azure-SSIS Integration Runtime. Подробнее см. в статье [Проверка пакетов служб SQL Server Integration Services (SSI) в Azure](ssis-azure-validate-packages.md).

Пример развертывания с использованием служб SSMS и мастера развертывания служб Integration Services см. в руководстве по [ развертыванию и запуску пакета служб SQL Server Integration Services (SSI) в Azure](ssis-azure-deploy-run-monitor-tutorial.md).

### <a name="version-support"></a>Поддерживаемые версии

В Azure можно развертывать пакеты, создаваемые в любых версиях SSIS. Если при развертывании пакета в Azure отсутствуют ошибки проверки, формат пакета автоматически обновляется до последней версии. Другими словами, пакет будет всегда обновлен до последней версии SSIS.

### <a name="run-packages"></a>Выполнение пакетов

Вам доступны несколько методов запуска пакетов MSSQL Integration Services, развернутых в Azure. Подробнее см. в статье [Выполнение пакетов служб SQL Server Integration Services (SSI), развернутых в Azure](ssis-azure-run-packages.md).

### <a name="run-packages-in-an-azure-data-factory-pipeline"></a>Выполнение пакетов в конвейере фабрики данных Azure

Чтобы выполнить пакет MSSQL Integration Services в конвейере Фабрики данных Azure, используйте действие "Выполнение пакета служб SSI". Дополнительные сведения см. в статье [Выполнение пакета служб SSIS с помощью действия "Выполнение пакета служб SSIS" в фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity).

Если вы запускаете пакет в конвейере фабрики данных с помощью действия "Выполнение пакета служб SSI", вы можете передать значения в пакет во время выполнения. Чтобы передать одно или несколько значений во время выполнения, создайте среды выполнения служб MSSQL Integration Services в SSISDB с помощью SQL Server Management Studio (SSM). В каждой среде создайте переменные и присвойте значения, которые соответствуют параметрам для проектов или пакетов. Настройте пакеты служб SSIS в среде SSMS, чтобы связать эти переменные среды с параметрами проекта или пакета. Если пакеты выполняются в конвейере, переключайтесь между средами, указывая пути к разным средам на вкладке "Параметры" пользовательского интерфейса действия "Выполнение пакета служб SSI". Дополнительные сведения о средах SSI см. в статье [Создание и сопоставление серверной среды](../packages/deploy-integration-services-ssis-projects-and-packages.md#create-and-map-a-server-environment).

## <a name="monitor-packages"></a>Мониторинг пакетов

Для отслеживания запускаемых пакетов вы можете использовать в SSMS следующие средства отчетности.
-   Щелкните базу данных **SSISDB** правой кнопкой мыши и выберите пункт **Активные операции**, чтобы открыть диалоговое окно **Активные операции**.
-   Выберите пакет в обозревателе объектов, щелкните его правой кнопкой мыши, выберите пункт **Отчеты**, затем — **Стандартные отчеты** и **Все выполнения**.

Сведения о мониторинге Azure-SSIS Integration Runtime: [Мониторинг Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime).

## <a name="schedule-packages"></a>Планирование выполнения пакетов
Запланировать запуск пакетов, развернутых в Azure, можно разными средствами. Подробнее см. в статье [Планирование выполнения пакетов служб SQL Server Integration Services (SSI), развернутых в Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Следующие шаги
Чтобы приступить к работе с рабочими нагрузками служб SSIS в Azure, ознакомьтесь со следующими статьями:
-   [Учебник. Развертывание и выполнение пакета служб SQL Server Integration Services (SSI) в Azure](ssis-azure-deploy-run-monitor-tutorial.md)
-   [Подготовка Integration Runtime Azure – SSI в Фабрике данных Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)

---
title: Перенос рабочих нагрузок SQL Server Integration Services в облако | Документы Майкрософт
ms.date: 05/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e3c8b39ac59f3ac6bddd985de12602f498e1ed97
ms.sourcegitcommit: b5ab9f3a55800b0ccd7e16997f4cd6184b4995f9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/23/2018
ms.locfileid: "34455468"
---
# <a name="lift-and-shift-sql-server-integration-services-workloads-to-the-cloud"></a>Перенос рабочих нагрузок SQL Server Integration Services в облако
Пакеты и рабочие нагрузки служб SQL Server Integration Services (SSIS) теперь можно переносить в облако Azure.
-   Храните проекты и пакеты служб SSIS и управляйте ими в базе данных каталога SSIS (SSISDB), размещенной в базе данных SQL Azure или в управляемом экземпляре базы данных SQL (предварительная версия).
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
-   Для Visual Studio 2015 — 17.2 или более поздняя версия.

Сведения о необходимых компонентах Azure-SSIS Integration Runtime: [Развертывание пакетов SQL Server Integration Services в Azure — предварительные требования](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure#prerequisites).

> [!NOTE]
> На этапе общедоступной предварительной версии среда Azure-SSIS Integration Runtime доступна не во всех регионах. Сведения о поддерживаемых регионах см. на странице [Доступность продуктов по регионам — Microsoft Azure](https://azure.microsoft.com/regions/services/).

## <a name="provision-ssis-on-azure"></a>Подготовка служб SSIS к работе в Azure

Перед тем как развертывать и выполнять пакеты SSIS в Azure, необходимо подготовить базу данных каталога SSIS (SSISDB) и среду Azure-SSIS Integration Runtime. Выполните подготовку согласно инструкциям в следующей статье: [Развертывание пакетов SQL Server Integration Services в Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure).

При подготовке среды Azure-SSIS IR вы можете осуществлять вертикальное и горизонтальное масштабирование, указывая значения для следующих параметров:
-   размер узла (включая число ядер) и число узлов в кластере;
-   существующий экземпляр базы данных SQL Azure для размещения базы данных каталога SSIS (SSISDB) и уровень обслуживания базы данных;
-   максимальное число параллельных выполнений в каждом узле.

Дополнительные сведения о производительности: [Настройка высокого уровня производительности в Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/configure-azure-ssis-integration-runtime-performance).

## <a name="design-packages"></a>Проектирование пакетов

Вы можете продолжать **проектировать и создавать пакеты** в локальной среде в средствах SSDT или в Visual Studio с установленными средствами SSDT.

### <a name="connect-to-data-sources"></a>Подключение к источникам данных

Дополнительные сведения о подключении к локальным источникам данных из облака с использованием **проверки подлинности Windows** см. в разделе [Подключение к локальным источникам данных и общим папкам Azure с помощью проверки подлинности Windows](ssis-azure-connect-with-windows-auth.md).

Дополнительные сведения о подключении к файлам и общим папкам см. в разделе [Хранение файлов в общих папках в локальной среде и в Azure с SSIS и их извлечение](ssis-azure-files-file-shares.md).

### <a name="available-ssis-components"></a>Доступные компоненты SSIS

При подготовке экземпляра базы данных SQL для размещения базы данных SSISDB также устанавливаются пакет дополнительных компонентов Azure для служб SSIS и распространяемый компонент Access. Эти компоненты обеспечивают подключение к различным источникам данных **Azure**, файлам **Excel и Access**, а также источникам данных, поддерживаемым встроенными компонентами.

Также можно установить дополнительные компоненты. Дополнительные сведения см. в разделе [Выборочная установка среды выполнения интеграции Azure-SSIS](/azure/articles/data-factory/how-to-configure-azure-ssis-ir-custom-setup.md).

Если вы независимый поставщик программного обеспечения, вы можете обновить установку лицензированных компонентов, чтобы сделать их доступными в Azure. Дополнительные сведения: [Разработка платных или лицензируемых пользовательских компонентов для Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/how-to-develop-azure-ssis-ir-licensed-components).

### <a name="transaction-support"></a>Поддержка транзакций

При использовании локальных виртуальных машин SQL Server и виртуальных машин Azure вы можете применять транзакции из координатора распределенных транзакций (Майкрософт) — MSDTC. Чтобы настроить MSDTC на каждом узле Azure-SSIS Integration Runtime, используйте функцию пользовательской настройки. Дополнительные сведения см. в разделе [Выборочная установка среды выполнения интеграции Azure-SSIS](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup).

При использовании базы данных SQL Azure вы можете применять только эластичные транзакции. Дополнительные сведения: [Распределенные транзакции в облачных базах данных](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-transactions-overview).

## <a name="deploy-and-run-packages"></a>Развертывание и запуск пакетов

**Модель развертывания**. Для проектов, развертываемых в базе данных SSISDB в Azure, необходимо использовать **модель развертывания проектов**, а не модель развертывания пакетов.

**Параметры развертывания и выполнения**. Для развертывания проектов и запуска пакетов в Azure можно использовать одно из знакомых средств и скриптов:
-   SQL Server Management Studio (SSMS)
-   Transact-SQL (в SSMS, Visual Studio Code или другом средстве)
-   Программа командной строки
-   PowerShell
-   C# и объектная модель управления служб SSIS

**Подключение к SSISDB**. **Имя базы данных SQL**, в которой размещается база данных SSISDB, станет первой частью четырехкомпонентного имени, которое применяется при развертывании и запуске пакетов из SSDT и SSMS в следующем формате: `<sql_database_name>.database.windows.net`. Дополнительные сведения о подключении к базе данных каталога SSIS в Azure: [Подключение к базе данных каталога SSISDB в Azure](ssis-azure-connect-to-catalog-database.md).

Чтобы приступить к работе, ознакомьтесь со статьей [Развертывание, запуск и отслеживание пакета служб SSIS в Azure](ssis-azure-deploy-run-monitor-tutorial.md).

## <a name="monitor-packages"></a>Мониторинг пакетов
Для отслеживания запускаемых пакетов в SSMS вы можете использовать следующие аналитические средства.
-   Щелкните базу данных **SSISDB** правой кнопкой мыши и выберите пункт **Активные операции**, чтобы открыть диалоговое окно **Активные операции**.
-   Выберите пакет в обозревателе объектов, щелкните его правой кнопкой мыши, выберите пункт **Отчеты**, затем — **Стандартные отчеты** и **Все выполнения**.

Сведения о мониторинге Azure-SSIS Integration Runtime: [Мониторинг Azure-SSIS Integration Runtime](https://docs.microsoft.com/azure/data-factory/monitor-integration-runtime#azure-ssis-integration-runtime).

## <a name="schedule-packages"></a>Планирование выполнения пакетов
Запланировать запуск пакетов, хранящихся в базе данных SQL Azure, можно разными средствами. Дополнительные сведения см. в разделе [Планирование выполнения пакета служб SSIS в Azure](ssis-azure-schedule-packages.md).

## <a name="next-steps"></a>Следующие шаги
Чтобы приступить к работе с рабочими нагрузками служб SSIS в Azure, ознакомьтесь со следующими статьями:
-   [Развертывание пакетов SQL Server Integration Services в Azure](https://docs.microsoft.com/azure/data-factory/tutorial-deploy-ssis-packages-azure)
-   [Развертывание, запуск и отслеживание пакета служб SSIS в Azure](ssis-azure-deploy-run-monitor-tutorial.md)

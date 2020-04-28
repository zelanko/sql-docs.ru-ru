---
title: Параметр воспроизведения (средство администрирования распределенного воспроизведения) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7ffe6a854e24240c6298dfbf7b4c195d787e07c7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "78172093"
---
# <a name="replay-option-distributed-replay-administration-tool"></a>Параметр воспроизведения (средство администрирования распределенного воспроизведения)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Средство `DReplay.exe`администрирования распределенное воспроизведение — это средство командной строки, которое можно использовать для взаимодействия с контроллером распределенного воспроизведения. В этом разделе описываются параметр командной строки **replay** и соответствующий синтаксис.

 Параметр **replay** инициирует стадию воспроизведения события, на которой контроллер отправляет данные воспроизведения указанным клиентам, запускает распределенное воспроизведение и синхронизирует клиенты. При необходимости каждый клиент, участвующий в воспроизведении, может записывать последовательность воспроизведения и сохранять получившиеся файлы трассировки в локальном кэше.

 ![Значок ссылки на раздел](../../database-engine/media/topic-link.gif "Значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых в синтаксисе средства администрирования, см. в разделе [Синтаксические обозначения в Transact-SQL (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).

## <a name="syntax"></a>Синтаксис

```

      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]
    [-starget_server] -wclients [-cconfig_file]
    [-fstatus_interval]
```

#### <a name="parameters"></a>Параметры
 *контроллер* **-m** указывает имя компьютера контроллера. Локальный компьютер можно указать как «`localhost`» или «`.`».

 Если параметр **-m** не задан, то используется локальный компьютер.

 **-d** *controller_working_dir* указывает каталог на контроллере, где будет храниться промежуточный файл. Параметр **-d** является обязательным.

 К нему предъявляются следующие требования.

-   Каталог должен находиться на контроллере.

-   Необходимо указать полный путь, начиная с буквы диска (например, `c:\WorkingDir`).

-   Путь не должен завершаться обратной косой чертой «`\`».

-   Пути в формате UNC не поддерживаются.

 **-o** Захватывает действие воспроизведения клиентов и сохраняет его в результирующий файл трассировки по пути, `<ResultDirectory>` `DReplayClient.xml`указанному в элементе в файле конфигурации клиента.

 Если параметр **-o** не указан, результирующий файл трассировки не создается. В конце воспроизведения консоль возвращает сводные данные, но остальная статистика воспроизведения недоступна.

 **-s** *target_server* указывает целевой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым должна воспроизводиться Распределенная рабочая нагрузка. Этот параметр необходимо задать в формате **имя_сервера[\имя_экземпляра]**.

 Недопустимо использовать в качестве целевого сервера «`localhost`» или «`.`».

 Параметр **-s** не является обязательным, если элемент `<Server>` задан в секции `<ReplayOptions>` файла конфигурации воспроизведения `DReplay.exe.replay.config`.

 Если используется параметр **-s** , элемент `<Server>` в секции `<ReplayOptions>` файла конфигурации воспроизведения будет игнорироваться.

 **-w** *Клиенты* . Этот обязательный параметр является разделенным запятыми (без пробелов), указывающими имена компьютеров клиентов, которые должны участвовать в распределенном воспроизведении. IP-адреса недопустимы. Помните, что клиенты должны быть уже зарегистрированы на контроллере.

> [!NOTE]
>  Каждый клиент регистрируется на контроллере, который указывается в файле конфигурации клиента при запуске службы клиента.

 **-c** *config_file* — это полный путь к файлу конфигурации воспроизведения; используется для указания расположения, когда оно хранится в другом расположении.

 Параметр **-c** не является обязательным, если будут использоваться значения по умолчанию файла конфигурации воспроизведения `DReplay.exe.replay.config`.

 **-f** *status_interval* указывает частоту (в секундах) вывода состояния.

 Если параметр **-f** не задан, интервал по умолчанию составляет 30 секунд.

## <a name="examples"></a>Примеры
 В данном примере распределенное воспроизведение наследует большую часть своего поведения из измененного файла конфигурации воспроизведения `DReplay.exe.replay.config`.

-   Параметр **-m** указывает, что в качестве контроллера выступает компьютер `controller1` . Имя компьютера нужно указывать, если служба контроллера работает на другом компьютере.

-   Параметр **-d** указывает расположение промежуточного файла `c:\WorkingDir`на контроллере.

-   Параметр **-o** указывает, что каждый заданный клиент регистрирует действие воспроизведения и сохраняет его в результирующем файле трассировки. Примечание. С помощью элемента `<ResultTrace>` файла конфигурации можно указать, следует ли записывать количество строк и результирующий набор.

-   Параметр **-w** указывает, что компьютеры `client1` – `client4` являются клиентами распределенного воспроизведения.

-   Параметр **-c** указывает на измененный файл конфигурации `DReplay.exe.replay.config`.

-   Параметр **-s** не является обязательным, потому что элемент `<Server>` задан в элементе `<ReplayOptions>` файла конфигурации воспроизведения `DReplay.exe.replay.config`.

 Этап воспроизведения событий инициируется следующим синтаксисом, когда средство администрирования запускается не на контроллере:

```
dreplay replay -m controller1 -d c:\WorkingDir -o -w client1,client2,client3,client4 -c c:\DReplay.exe.replay.config
```

 Чтобы установить синхронный режим последовательного выполнения, элементу `<SequencingMode>` в файле `DReplay.exe.replay.config` нужно присвоить значение `synchronization`. Раздел `<ResultTrace>` файла конфигурации воспроизведения изменен для указания записи количества строк. Эти изменения показаны в следующем примере XML-кода:

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance</Server>
        <SequencingMode>synchronization</SequencingMode>
        <ConnectTimeScale></ConnectTimeScale>
        <ThinkTimeScale></ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

 Чтобы установить режим нагрузки последовательного выполнения, элементу `<SequencingMode>` в файле `DReplay.exe.replay.config` нужно присвоить значение `stress`. Элементам `<ConnectTimeScale>` и `<ThinkTimeScale>` присваивается значение `50` (что означает 50 процентов). Дополнительные сведения о времени соединения и времени обработки см. в разделе [Настройка распределенного воспроизведения](configure-distributed-replay.md). Эти изменения показаны в следующем примере XML-кода:

```
<?xml version='1.0'?>
<Options>
    <ReplayOptions>
        <Server>server_name\replay_target_instance_name</Server>
        <SequencingMode>stress</SequencingMode>
        <ConnectTimeScale>50</ConnectTimeScale>
        <ThinkTimeScale>50</ThinkTimeScale>
        <HealthmonInterval>60</HealthmonInterval>
        <QueryTimeout>3600</QueryTimeout>
        <ThreadsPerClient></ThreadsPerClient>
    </ReplayOptions>
    <OutputOptions>
        <ResultTrace>
            <RecordRowCount>Yes</RecordRowCount>
            <RecordResultSet>No</RecordResultSet>
        </ResultTrace>
    </OutputOptions>
</Options>
```

## <a name="permissions"></a>Разрешения
 Средство администрирования должно запускаться как интерактивный пользователь, с учетной записью локального пользователя или пользователя домена. Для использования учетной записи локального пользователя средство администрирования и контроллер должны быть запущены на одном компьютере.

 Дополнительные сведения см. в статье [Distributed Replay Security](distributed-replay-security.md).

## <a name="see-also"></a>См. также:
 [Воспроизведение данных трассировки](replay-trace-data.md) [проверьте результаты воспроизведения](review-the-replay-results.md) [SQL Server распределенное воспроизведение](sql-server-distributed-replay.md) [настроить](configure-distributed-replay.md) [форум распределенное воспроизведение SQL Server распределенное воспроизведение](https://social.technet.microsoft.com/Forums/sl/sqldru/) [, используя распределенное воспроизведение для нагрузочного тестирования SQL Server. часть 2](https://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx) [с помощью распределенное воспроизведение для нагрузочного тестирования SQL Server. часть 1](https://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)



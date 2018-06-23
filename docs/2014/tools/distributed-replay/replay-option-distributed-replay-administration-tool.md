---
title: Параметр воспроизведения (средство администрирования распределенного воспроизведения) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7bce6a5-d414-488d-a3cd-50c1c62019c4
caps.latest.revision: 24
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: e9829a1b3df098be4637921bb9b779635d24376b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36179974"
---
# <a name="replay-option-distributed-replay-administration-tool"></a>Параметр воспроизведения (средство администрирования распределенного воспроизведения)
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Распределенного воспроизведения средство администрирования `DReplay.exe`, это средство командной строки, можно использовать для взаимодействия с контроллером распределенного воспроизведения. В этом разделе описываются параметр командной строки **replay** и соответствующий синтаксис.  
  
 Параметр **replay** инициирует стадию воспроизведения события, на которой контроллер отправляет данные воспроизведения указанным клиентам, запускает распределенное воспроизведение и синхронизирует клиенты. При необходимости каждый клиент, участвующий в воспроизведении, может записывать последовательность воспроизведения и сохранять получившиеся файлы трассировки в локальном кэше.  
  
 ![Topic link icon](../../database-engine/media/topic-link.gif "Значок ссылки на раздел") Дополнительные сведения о синтаксических обозначениях, используемых в синтаксисе средства администрирования, см. в разделе [Синтаксические обозначения в Transact-SQL (Transact-SQL)](/sql/t-sql/language-elements/transact-sql-syntax-conventions-transact-sql).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
      dreplay replay [-mcontroller] -dcontroller_working_dir [-o]  
    [-starget_server] -wclients [-cconfig_file]  
    [-fstatus_interval]  
```  
  
#### <a name="parameters"></a>Параметры  
 **-m** *controller*  
 Задает имя компьютера для контроллера. Локальный компьютер можно указать как «`localhost`» или «`.`».  
  
 Если параметр **-m** не задан, то используется локальный компьютер.  
  
 **-d** *рабочий_каталог_контроллера*  
 Указывает каталог на контроллере, где будет сохранен промежуточный файл. Параметр **-d** является обязательным.  
  
 К нему предъявляются следующие требования.  
  
-   Каталог должен находиться на контроллере.  
  
-   Необходимо указать полный путь, начиная с буквы диска (например, `c:\WorkingDir`).  
  
-   Путь не должен завершаться обратной косой чертой «`\`».  
  
-   Пути в формате UNC не поддерживаются.  
  
 **-o**  
 Отслеживает действие воспроизведения клиента и сохраняет его в итоговом файле трассировки в каталоге, указанном элементом `<ResultDirectory>` в файле конфигурации клиента `DReplayClient.xml`.  
  
 Если параметр **-o** не задан, результирующий файл трассировки не создается. В конце воспроизведения консоль возвращает сводные данные, но остальная статистика воспроизведения недоступна.  
  
 **-s** *целевой_сервер*  
 Указывает целевой экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором требуется воспроизвести распределенную рабочую нагрузку. Этот параметр необходимо задать в формате **имя_сервера[\имя_экземпляра]**.  
  
 Недопустимо использовать в качестве целевого сервера «`localhost`» или «`.`».  
  
 Параметр **-s** не является обязательным, если элемент `<Server>` задан в секции `<ReplayOptions>` файла конфигурации воспроизведения `DReplay.exe.replay.config`.  
  
 Если используется параметр **-s** , элемент `<Server>` в секции `<ReplayOptions>` файла конфигурации воспроизведения будет игнорироваться.  
  
 **-w** *клиенты*  
 Требуемым параметром является список с разделителями-запятыми (без пробелов), содержащий имена компьютеров клиентов, которые должны участвовать в распределенном воспроизведении. IP-адреса недопустимы. Помните, что клиенты должны быть уже зарегистрированы на контроллере.  
  
> [!NOTE]  
>  Каждый клиент регистрируется на контроллере, который указывается в файле конфигурации клиента при запуске службы клиента.  
  
 **-c** *файл_конфигурации*  
 Полный путь к файлу конфигурации воспроизведения; используется для указания расположения, если оно отличается от расположения по умолчанию.  
  
 Параметр **-c** не является обязательным, если будут использоваться значения по умолчанию файла конфигурации воспроизведения `DReplay.exe.replay.config`.  
  
 **-f** *интервал_состояния*  
 Указывает частоту (в секундах) отображения состояния.  
  
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
  
## <a name="see-also"></a>См. также  
 [Воспроизведение данные трассировки](replay-trace-data.md)   
 [Просмотр результатов воспроизведения](review-the-replay-results.md)   
 [Распределенное воспроизведение SQL Server](sql-server-distributed-replay.md)   
 [Настройка распределенного воспроизведения](configure-distributed-replay.md)   
 [Форум о распределенном воспроизведении SQL Server](http://social.technet.microsoft.com/Forums/sl/sqldru/)   
 [Использование распределенного воспроизведения для нагрузочного теста SQL Server. Часть 2](http://blogs.msdn.com/b/mspfe/archive/2012/11/14/using-distributed-replay-to-load-test-your-sql-server-part-2.aspx)   
 [Использование распределенного воспроизведения для нагрузочного теста SQL Server. Часть 1](http://blogs.msdn.com/b/mspfe/archive/2012/11/08/using-distributed-replay-to-load-test-your-sql-server-part-1.aspx)  
  
  

---
title: Заметки о выпуске SQL Server 2016 | Документация Майкрософт
ms.date: 03/14/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: ''
ms.component: sql-non-specified
ms.reviewer: ''
ms.suite: sql
ms.custom: ''
ms.technology:
- server-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
caps.latest.revision: ''
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 1a6d422098fdacb3a7bc6392b99fe63bb25c2c36
ms.sourcegitcommit: 6e16d1616985d65484c72f5e0f34fb2973f828f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/16/2018
---
# <a name="sql-server-2016-release-notes"></a>Заметки о выпуске SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
  В этой статье описываются ограничения и проблемы, связанные с выпусками SQL Server 2016, включая пакеты обновления. Сведения о новых возможностях см. в разделе [Что нового в SQL Server 2016](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2016).

> [![Скачать на странице центра оценки](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) Скачать SQL Server 2016 на странице **[центра оценки](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**
>
> [Маленький значок виртуальной машины Azure![](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Есть ли учетная запись Azure?  Тогда перейдите **[сюда](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** , чтобы запустить виртуальную машину с уже установленным SQL Server 2016 с пакетом обновления 1 (SP1).
>
> [![Скачать SSMS](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) Чтобы получить последнюю версию среды SQL Server Management Studio, перейдите на страницу **[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)**.

## <a name="bkmk_2016sp1"></a>SQL Server 2016 с пакетом обновления 1 (SP1)
![info_tip](../sql-server/media/info-tip.png) В SQL Server 2016 с пакетом обновления 1 (SP1) входят все исправления вплоть до накопительного пакета обновления 3 для SQL Server 2016 RTM, включая обновление для системы безопасности MS16-136. Этот выпуск содержит все исправления из накопительных пакетов обновления для SQL Server 2016 до накопительного пакета обновления 3 включительно, а также обновление для системы безопасности MS16-136, выпущенное 8 ноября 2016 г. 

В выпусках Standard, Web, Express и Local DB продукта SQL Server с пакетом обновления 1 (SP1) доступны следующие функции (если не указано иное):
- Always Encrypted
- Отслеживание измененных данных (недоступно в выпуске Express)
- columnstore
- Сжатие
- Динамическое маскирование данных
- Аудит мелких фрагментов данных
- Выполняющаяся в памяти OLTP (недоступна в выпуске Local DB)
- Несколько контейнеров файлового потока (недоступно в выпуске Local DB)
- Секционирование
- PolyBase
- Безопасность на уровне строк

В приведенной ниже таблице представлена сводка основных улучшений в SQL Server 2016 с пакетом обновления 1 (SP1).

|Компонент|Description|Дополнительные сведения|
|---|---|---|
|Массовая вставка в кучи с автоматическим использованием указания TABLOCK, если установлен флаг трассировки 715| Флаг трассировки 715 включает блокировку таблицы для операций массовой загрузки в кучу без некластеризованных индексов.|[Перенос рабочих нагрузок SAP в SQL Server производится в 2,5 раза быстрее](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|CREATE или ALTER|Развертывание объектов, таких как хранимые процедуры, триггеры, определяемые пользователем функции и представления.|[Блог по ядру СУБД SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/11/17/create-or-alter-another-great-language-enhancement-in-sql-server-2016-sp1/)|
|Поддержка DROP TABLE для репликации|Поддержка DROP TABLE DDL для репликации позволяет удалять статьи репликации.|[Статья базы знаний 3170123](https://support.microsoft.com/help/3170123/supports-drop-table-ddl-for-articles-that-are-included-in-transactiona)|
|Подписывание драйвера RsFx файлового потока|Драйвер RsFx файлового потока подписывается и сертифицируется с помощью портала "Информационная панель Центра разработки оборудования для Windows" (портал разработчика), что позволяет без проблем устанавливать драйвер RsFx файлового потока для SQL Server 2016 с пакетом обновления 1 (SP1) в ОС Windows Server 2016 и Windows 10.|[Перенос рабочих нагрузок SAP в SQL Server производится в 2,5 раза быстрее](https://blogs.msdn.microsoft.com/sql_server_team/migrating-sap-workloads-to-sql-server-just-got-2-5x-faster/)|
|Разрешение LPIM в учетной записи службы SQL — программное определение|Администраторы баз данных могут программно определять, действует ли разрешение "Блокировка страниц в памяти" (LPIM) во время запуска службы.|[Выбор разработчика: программное определение наличия разрешений LPIM и IFI в SQL Server](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-programmatically-identify-lpim-and-ifi-privileges-in-sql-server)|
|Очистка отслеживания изменений вручную|Новая хранимая процедура очищает внутреннюю таблицу отслеживания изменений по требованию.| [Статья базы знаний 3173157](https://support.microsoft.com/help/3173157/adds-a-stored-procedure-for-the-manual-cleanup-of-the-change-tracking)|
|Параллельные изменения INSERT..SELECT в локальных временных таблицах|Новые параллельные операции INSERT в INSERT..SELECT.|[Группа консультантов по SQL Server](https://blogs.msdn.microsoft.com/sqlcat/2016/07/21/real-world-parallel-insert-what-else-you-need-to-know/)|
|Showplan XML|Расширенная диагностика, включающая предупреждение о временно предоставляемом буфере памяти, сведения о максимальном объеме памяти, предоставляемом для запроса, установленных флагах трассировки, а также другие диагностические данные. | [Статья базы знаний 3190761](https://support.microsoft.com/help/3190761/update-to-improve-diagnostics-by-expose-data-type-of-the-parameters-fo)|
|Память класса хранилища|Ускорьте обработку транзакций с помощью памяти класса хранилища в Windows Server 2016, которая позволяет на порядок сократить время фиксации транзакций.|[Блог по ядру СУБД SQL Server](https://blogs.msdn.microsoft.com/sqlserverstorageengine/2016/12/02/transaction-commit-latency-acceleration-using-storage-class-memory-in-windows-server-2016sql-server-2016-sp1/)|
|USE HINT|Используйте параметр запроса `OPTION(USE HINT('<option>'))` для изменения поведения оптимизатора запросов с помощью поддерживаемых указаний уровня запроса. В отличие от QUERYTRACEON, параметр USE HINT не требует привилегий администратора.|[Выбор разработчика: указания запроса USE HINT](https://blogs.msdn.microsoft.com/sql_server_team/developers-choice-use-hint-query-hints/)|
|Дополнения XEvent|Возможности диагностики, предоставляемые новыми расширенными событиями и счетчиками производительности, позволяют более эффективно устранять задержки.|[Расширенные события](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)|

Кроме того, обратите внимание на указанные ниже исправления.
- На основе отзывов администраторов баз данных и участников сообщества SQL начиная с SQL Server 2016 с пакетом обновления 1 (SP1) сообщения журнала, связанные с Hekaton, сведены к минимуму.
- Ознакомьтесь с новыми [флагами трассировки](https://docs.microsoft.com/en-us/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).
- Полные версии образцов баз данных WideWorldImporters работают с выпусками Standard и Express начиная с SQL Server 2016 с пакетом обновления 1 (SP1) и доступны в [Github]( https://github.com/Microsoft/sql-server-samples/releases/tag/wide-world-importers-v1.0). Вносить изменения в образцы не требуется. Резервные копии баз данных, созданные в версии RTM выпуска Enterprise, работают с выпусками Standard и Express в SQL Server 2016 с пакетом обновления 1 (SP1). 

После установки SQL Server 2016 с пакетом обновления 1 (SP1) может потребоваться перезагрузка. Мы рекомендуем запланировать и выполнить перезагрузку после установки SQL Server 2016 с пакетом обновления 1 (SP1).

### <a name="download-pages-and-more-information"></a>Страницы загрузки и дополнительные сведения

- [Скачать пакет обновления 1 (SP1) для Microsoft SQL Server 2016](https://www.microsoft.com/download/details.aspx?id=54276)
- [Выпущен SQL Server 2016 с пакетом обновления 1 (SP1)](https://blogs.msdn.microsoft.com/sqlreleaseservices/sql-server-2016-service-pack-1-sp1-released/)
- [Сведения о выпуске SQL Server 2016 с пакетом обновления 1 (SP1)](https://support.microsoft.com/kb/3182545)
- ![info_tip](../sql-server/media/info-tip.png) В [Центре обновления SQL Server](https://msdn.microsoft.com/library/ff803383.aspx) можно найти ссылки и сведения для всех поддерживаемых версий, включая пакеты обновления для [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 

##  <a name="bkmk_2016_ga"></a> SQL Server 2016 Release - General Availability (GA)
-   [Ядро СУБД (общедоступная версия)](#bkmk_ga_instalpatch) 
-   [Stretch Database (общедоступная версия)](#bkmk_ga_stretch)
-   [Хранилище запросов (общедоступная версия)](#bkmk_ga_query_store)
-   [Документация по продукту (общедоступная версия)](#bkmk_ga_docs)
 
### ![repl_icon_warn](../database-engine/availability-groups/windows/media/repl-icon-warn.gif) <a name="bkmk_ga_instalpatch"></a> Install Patch Requirement (GA) 
**Проблема и последствия для клиентов:** корпорация Майкрософт выявила проблему с двоичными файлами среды выполнения Microsoft VC++ 2013, которые SQL Server 2016 устанавливает в качестве необходимого компонента. Для исправления этой проблемы выпущено обновление. Если это обновление двоичных файлов среды выполнения VC не установлено, в SQL Server 2016 могут возникать проблемы с надежностью в определенных сценариях. Перед установкой SQL Server 2016 проверьте, требуется ли на вашем компьютере исправление, описываемое в статье [KB 3164398](http://support.microsoft.com/kb/3164398). Обновление также включено в [накопительный пакет обновления 1 (CU1) для SQL Server 2016 RTM](https://www.microsoft.com/download/details.aspx?id=53338). 

**Решение.** Используйте одно из следующих решений.

- Установите [обновление для Visual C++ 2013 и распространяемого пакета Visual C++ из статьи KB 3138367](http://support.microsoft.com/kb/3138367). Использование статьи KB является предпочтительным решением. Обновление можно установить до или после установки SQL Server 2016. 

    Если SQL Server 2016 уже установлен, выполните по порядку указанные ниже действия.

    1.  Скачайте соответствующий файл *vcredist_\*exe*.
    1.  Остановите службу SQL Server для всех экземпляров ядра СУБД.
    1.  Установите обновление **KB 3138367**.
    1.  Перезагрузите компьютер.
 

 - Установите  [критическое обновление для необходимых компонентов MSVCRT в SQL Server 2016, KB 3164398](http://support.microsoft.com/kb/3164398).  
 
    Обновление **KB 3164398**можно установить во время установки SQL Server, из Центра обновления Майкрософт или из Центра загрузки Майкрософт. 

    - **Во время установки SQL Server 2016:** если у компьютера, на котором запущена программа установки SQL Server, есть доступ к Интернету, программа установки SQL Server проверяет наличие обновления в процессе своего выполнения. Если вы подтвердите обновление, программа установки скачивает и обновляет двоичные файлы во время установки.

    - **Центр обновления Майкрософт:** обновление доступно в Центре обновления Майкрософт как критически важное обновление SQL Server 2016, не связанное с системой безопасности. После установки обновления через Центр обновления Майкрософт SQL Server 2016 потребует перезапустить сервер. 

    - **Центр загрузки:** наконец, обновление доступно в Центре загрузки Майкрософт. Вы можете скачать программный пакет обновления и установить его на серверах после установки SQL Server 2016. 


### <a name="bkmk_ga_stretch"></a>Stretch Database

#### <a name="problem-with-a-specific-character-in-a-database-or-table-name"></a>Проблема с определенным символом в имени базы данных или таблицы

**Проблема и последствия для клиентов:** попытка включить Stretch Database в базе данных или таблице завершается ошибкой. Эта проблема возникает, если имя объекта содержит символ, который при преобразовании из нижнего в верхний регистр считается другим символом. Примером символа, вызывающего эту проблему, может служить символ "ƒ" (который вводится с помощью кода ALT+159).

**Обходное решение.** Если вы хотите включить Stretch Database для базы данных или таблицы, единственным выходом является переименование объекта с целью удалить проблемный символ.

#### <a name="problem-with-an-index-that-uses-the-include-keyword"></a>Проблема с индексом, в котором используется ключевое слово INCLUDE

**Проблема и последствия для клиентов.** При попытке включить Stretch Database для таблицы с индексом, в котором используется ключевое слово INCLUDE для включения в индекс дополнительных столбцов, происходит ошибка.

**Обходное решение.** Удалите индекс, в котором используется ключевое слово INCLUDE, включите Stretch Database для таблицы, а затем снова создайте индекс. При этом следует соблюдать принятые в организации правила и политики обслуживания, чтобы влияние на работу пользователей таблицы было минимальным или нулевым.

### <a name="bkmk_ga_query_store"></a>Query Store

#### <a name="problem-with-automatic-data-cleanup-on-editions-other-than-enterprise-and-developer"></a>Проблема с автоматической очисткой данных в выпусках, отличных от Enterprise и Developer

 **Проблема и последствия для клиентов.** Автоматическая очистка данных завершается сбоем в выпусках, отличных от Enterprise и Developer. Поэтому, если не очищать данные вручную, пространство, используемое хранилищем запросов, с течением времени будет расти, пока не будет достигнуто настроенное предельное значение. Если эту проблему не решить, она также приведет к заполнению дискового пространства, выделенного для журналов ошибок, так как при каждой попытке очистки создается файл дампа. Период активации очистки зависит от частоты рабочей нагрузки, но не превышает 15 минут.

 **Обходное решение.** Если вы планируете использовать хранилище запросов в выпусках, отличных от Enterprise и Developer, необходимо явно отключить политики очистки. Это можно сделать либо в среде SQL Server Management Studio (на странице "Свойства базы данных"), либо с помощью скрипта Transact-SQL:

```ALTER DATABASE <database name> SET QUERY_STORE (OPERATION_MODE = READ_WRITE, CLEANUP_POLICY = (STALE_QUERY_THRESHOLD_DAYS = 0), SIZE_BASED_CLEANUP_MODE = OFF)```

Кроме того, рассмотрите варианты ручной очистки, чтобы избежать перехода хранилища запросов в режим "только для чтения". Например, выполняйте следующий запрос для периодической очистки всего дискового пространства:

```ALTER DATABASE <database name> SET QUERY_STORE CLEAR```

Кроме того, периодически выполняйте следующие процедуры хранилища запросов для очистки статистики времени выполнения, определенных запросов или планов:

- `sp_query_store_reset_exec_stats`

- `sp_query_store_remove_plan`

- `sp_query_store_remove_query`


###  <a name="bkmk_ga_docs"></a> Документация по продукту (общедоступная версия) 
 **Проблема и последствия для клиентов:** загружаемая версия документации по SQL Server 2016 пока недоступна. При использовании диспетчера библиотек справки для **установки содержимого из Интернета** вы увидите документацию по SQL Server 2012 и SQL Sever 2014, но не увидите документацию по SQL Server 2016.    
    
 **Обходное решение.** Используйте один из следующих способов.    
    
 ![Управление параметрами справки для SQL Server](../sql-server/media/docs-sql2016-managehelpsettings.png "Управление параметрами справки для SQL Server")    
    
-   Используйте вариант **Выбрать справку в сети или локальную справку** и настройте справку для "Я хочу использовать справку в сети".    
    
-   Используйте вариант **Установить содержимое из сети** и загрузите содержимое SQL Server 2014.    
    
 **Справка F1.** При нажатии клавиши F1 в [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] в браузере открывается веб-версия статьи справки F1. Проблема связана со справкой на основе браузера даже в том случае, если настроена или установлена локальная справка. 
     
**Обновление содержимого:**    
В SQL Server Management Studio и Visual Studio окно справки может перестать отвечать на запросы во время добавления документации. Чтобы устранить эту проблему, выполните указанные ниже действия. Сведения об этой проблеме см. в разделе [Окно справки Visual Studio зависает](https://msdn.microsoft.com/library/mt654096.aspx).    
    
* Откройте файл %LOCALAPPDATA%\Microsoft\HelpViewer2.2\HlpViewer_SSMS16_en-US.settings | HlpViewer_VisualStudio14_en-US.settings в Блокноте и измените дату в приведенном ниже коде на какую-либо дату в будущем.    
    
     
```    
     Cache LastRefreshed="12/31/2017 00:00:00"    
``` 

## <a name="additional-information"></a>Дополнительные сведения
+ [Установка SQL Server 2016](../database-engine/install-windows/installation-for-sql-server-2016.md)
+ [Ссылки и сведения для всех поддерживаемых версий в Центре обновления SQL Server](https://msdn.microsoft.com/library/ff803383.aspx)


[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]    

![MS_Logo_X-Small](../sql-server/media/ms-logo-x-small.png "MS_Logo_X-Small")    

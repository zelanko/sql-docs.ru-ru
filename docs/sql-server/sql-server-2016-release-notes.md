---
title: "Заметки о выпуске SQL Server 2016 | Документация Майкрософт"
ms.date: 02/27/2018
ms.prod: sql-non-specified
ms.prod_service: sql-non-specified
ms.service: 
ms.component: sql-non-specified
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- server-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- build notes
- release issues
ms.assetid: c64077a2-bec8-4c87-9def-3dbfb1ea1fb6
caps.latest.revision: 
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.workload: Active
ms.openlocfilehash: 6485ef83b940ab9d04b9406e461517d5254aec7f
ms.sourcegitcommit: 1a3584a60c12521ba5b4b12a18d8cb32b1f2d555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/28/2018
---
# <a name="sql-server-2016-release-notes"></a>Заметки о выпуске SQL Server 2016
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]
В этой статье описываются ограничения и проблемы, связанные с выпусками SQL Server 2016. Сведения о новых возможностях см. в разделе [Что нового в SQL Server 2016](https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-2016).

> [![Скачать на странице центра оценки](../includes/media/download2.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016) Скачать SQL Server 2016 на странице **[центра оценки](https://www.microsoft.com/evalcenter/evaluate-sql-server-2016)**
>
> [Маленький значок виртуальной машины Azure![](../includes/media/azure-vm.png)](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/) Есть ли учетная запись Azure?  Тогда перейдите **[сюда](https://azure.microsoft.com/marketplace/partners/microsoft/sqlserver2016sp1standardwindowsserver2016/)** , чтобы запустить виртуальную машину с уже установленным SQL Server 2016 с пакетом обновления 1 (SP1).
>
> [![Скачать SSMS](../includes/media/download2.png)](../ssms/download-sql-server-management-studio-ssms.md) Чтобы получить последнюю версию среды SQL Server Management Studio, перейдите на страницу **[Скачивание SQL Server Management Studio (SSMS)](../ssms/download-sql-server-management-studio-ssms.md)**.

## <a name="bkmk_2016sp1"></a>SQL Server 2016 с пакетом обновления 1 (SP1)
![info_tip](../sql-server/media/info-tip.png) SQL Server 2016 с пакетом обновления 1 (SP1) обновляет все выпуски и уровни служб SQL Server 2016 до версии SQL Server 2016 с пакетом обновления 1 (SP1). Помимо исправлений, перечисленных в этой статье, SQL Server 2016 с пакетом обновления 1 (SP1) содержит исправления, включенные в SQL Server 2016 с накопительным пакетом обновления 1 (CU1), накопительным пакетом обновления 2 (CU2) и накопительным пакетом обновления 3 (CU3).

- [Страница скачивания SQL Server 2016 с пакетом обновления 1 (SP1)](https://www.microsoft.com/download/details.aspx?id=54276)
- [SQL Server 2016 Service Pack 1 release information](https://support.microsoft.com/kb/3182545) (Сведения о выпуске SQL Server 2016 с пакетом обновления 1). В этой статье содержатся отдельные ошибки и проблемы, исправленные или устраненные в пакете обновления 1.
 - ![info_tip](../sql-server/media/info-tip.png) См. статью [Центр обновления SQL Server](https://msdn.microsoft.com/library/ff803383.aspx), где приведены ссылки и сведения для всех поддерживаемых версий, включая пакеты обновления для [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 

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

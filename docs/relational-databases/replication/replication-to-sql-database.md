---
title: "Репликация базы данных SQL | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "06/29/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Репликация базы данных SQL"
  - "репликация, база данных SQL"
ms.assetid: e8484da7-495f-4dac-b38e-bcdc4691f9fa
caps.latest.revision: 15
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 15
---
# Репликация базы данных SQL
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] можно настроить репликацию для [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)].  
  
 **Поддерживаемые конфигурации:**  
  
-    [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Может быть экземпляром [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] под управлением локальной или экземпляр [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виртуальной машине Azure в облаке. Дополнительные сведения см. в статье [Обзор SQL Server на виртуальных машинах Azure](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/).  
  
-   [!INCLUDE[ssSDS](../../includes/sssds-md.md)] должна быть подписчиком с принудительной подпиской издателя [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   База данных распространителя и агенты репликации не могут размещаться в [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
-   Поддерживается односторонняя репликация транзакций и создание моментальных снимков. Одноранговая репликация транзакций и репликация слиянием не поддерживаются.  
  
## Версии  
 Минимальные требования к версиям издателя и распространителя:  
  
-   [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] с пакетом обновления 1 (SP1) CU3  
  
-   [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] RTM CU10  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] с пакетом обновления 2 (SP2) CU8  
  
-   [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] , ожидаемая в версии с пакетом обновления 3 (SP3)  
  
 Попытка настроить репликацию с помощью более старой версии может возникать ошибка номер MSSQL_REPL20084 (процесс не удалось подключиться к подписчику.) и MSSQL_REPL40532 (не удается открыть сервер \< имя> запрашиваемую именем входа. Ошибка входа").  
  
 Версия подписчика [!INCLUDE[ssSDS](../../includes/sssds-md.md)] должна быть не ниже 12; сам подписчик может находиться в любом регионе.  
  
 Чтобы использовать все возможности [!INCLUDE[ssSDS](../../includes/sssds-md.md)] необходимо использовать последние версии [SQL Server Management Studio](https://msdn.microsoft.com/library/mt238290.aspx) и [SQL Server Data Tools](https://msdn.microsoft.com/library/mt204009.aspx).  
  
## Замечания  
 Репликацию можно настроить с помощью [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] или путем выполнения инструкций [!INCLUDE[tsql](../../includes/tsql-md.md)] на издателе. Настроить репликацию с помощью портала [!INCLUDE[ssSDS](../../includes/sssds-md.md)] нельзя.  
  
 Для подключения к [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в репликации можно использовать только учетные данные для входа [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
 Реплицируемая таблица должна иметь первичный ключ.  
  
 Вам понадобится существующая подписка Azure и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] версии 12.  
  
 В одной публикации [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] может поддерживать оба [!INCLUDE[ssSDS](../../includes/sssds-md.md)] и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (локальных и [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] в виртуальной машине Azure) подписчиков.  
  
 Управление репликацией, мониторинг и устранение неполадок должны выполняться из локальной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
 Поддерживаются только принудительные подписки на [!INCLUDE[ssSDS](../../includes/sssds-md.md)] .  
  
 Только `@subscriber_type = 0` поддерживается в **sp_addsubscription** для базы данных SQL.  
  
 [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не поддерживает двусторонний обмен, немедленно, обновляемых или одноранговой репликации.  
  
## Архитектура репликации  
 ![replication-to-sql-database](../../relational-databases/replication/media/replication-to-sql-database.png "replication-to-sql-database")  
  
## Сценарии  
  
#### Сценарий стандартной репликации  
  
1.  Создать публикацию репликации транзакций на локальной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных.  
  
2.  На локальной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] использовать **мастера создания подписки** или [!INCLUDE[tsql](../../includes/tsql-md.md)] инструкции для создания принудительной подписке для [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
3.  В качестве исходного набора данных обычно используется моментальный снимок, созданный агентом моментальных снимков, который распространяется и применяется агентом распространителя. Исходный набор данных может также предоставляться через резервную копию или другие средства, например [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
#### Сценарии переноса данных  
  
1.  Использовать репликацию транзакций для репликации данных из локальной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] базы данных [!INCLUDE[ssSDS](../../includes/sssds-md.md)].  
  
2.  Перенаправление клиента или среднего уровня приложения, чтобы обновить [!INCLUDE[ssSDS](../../includes/sssds-md.md)] копии.  
  
3.  Остановка обновления версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] таблицы и удаление публикации.  
  
## Ограничения  
 В подписках [!INCLUDE[ssSDS](../../includes/sssds-md.md)] не поддерживаются следующие функции:  
  
-   Копирование сопоставления групп файлов  
  
-   Копирование схем секционирования таблиц  
  
-   Копирование схем секционирования индексов  
  
-   Копирование определяемой пользователем статистики  
  
-   Копирование привязок по умолчанию  
  
-   Копирование привязок правил  
  
-   Копирование полнотекстовых индексов  
  
-   Копирование XML XSD  
  
-   Копирование XML-индексов  
  
-   Копирование разрешений  
  
-   Копирование пространственных индексов  
  
-   Копирование отфильтрованных индексов  
  
-   Копирование атрибутов сжатия данных  
  
-   Копирование атрибутов разреженных столбцов  
  
-   Преобразование типа filestream в типы данных MAX  
  
-   Преобразование типа hierarchyId в типы данных MAX  
  
-   Преобразование пространственных типов в типы данных MAX  
  
-   Копирование расширенных свойств  
  
-   Копирование разрешений  
  
 Ограничения, подлежащие определению:  
  
-   Копирование параметров сортировки  
  
-   Выполнение в сериализованной транзакции хранимой процедуры  
  
## Примеры  
 Создание публикации и принудительной подписки. Дополнительные сведения см. в разделе:  
  
-   [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)  
  
-   [Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md) с помощью [!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)] имя логического сервера в качестве подписчика (например **N'azuresqldbdns.database.windows.net "**) и [!INCLUDE[ssSDS](../../includes/sssds-md.md)] имя, что и целевой базы данных (например **AdventureWorks**).  
  
## См. также:  
 [Создание публикации](../../relational-databases/replication/publish/create-a-publication.md)   
 [Создание принудительной подписки](../../relational-databases/replication/create-a-push-subscription.md)   
 [Типы репликации](../../relational-databases/replication/types-of-replication.md)   
 [Мониторинг и #40; Репликация & #41;](../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Инициализация подписки](../../relational-databases/replication/initialize-a-subscription.md)  
  
  
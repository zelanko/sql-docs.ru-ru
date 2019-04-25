---
title: Репликация SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], about
- replication [SQL Server]
ms.assetid: 3a5f4592-3c61-4b4d-9ceb-39716aeeba41
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: be03754ea8eeb61d838357667da6e37e1be6bc31
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62626158"
---
# <a name="sql-server-replication"></a>Репликация SQL Server
  Репликация представляет собой набор технологий копирования и распространения данных и объектов баз данных между базами данных, а также синхронизации баз данных для поддержания согласованности. Используя репликацию, можно распространять данные в различные расположения, а также удаленным или мобильным пользователям по локальным или глобальным сетям посредством коммутируемого соединения, по беспроводным соединениям и через Интернет.  
  
 Репликация транзакций обычно используется в сценариях «сервер-сервер», для которых необходима высокая пропускная способность, в том числе улучшение масштабируемости и доступности, хранение и протоколирование данных, интеграция данных с нескольких сайтов, объединение разнородных данных, автономная обработка пакетов. Репликация слиянием разработана в основном для мобильных приложений или распределенных серверных приложений, в которых возможно возникновение конфликтов данных. Обычные сценарии включают обмен данными с мобильными пользователями, клиентские приложения точки продажи (POS) и интеграцию данных с нескольких сайтов. Репликация моментальных снимков используется для обеспечения начального набора данных для репликации транзакций и репликации слиянием; она также может применяться при необходимости выполнения полного обновления данных. Располагая этими тремя типами репликации, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] представляет собой мощную и гибкую систему для синхронизации данных уровня предприятия. Репликация на SQLCE 3.5 и SQLCE 4.0 поддерживается и для [!INCLUDE[win8srv](../../includes/win8srv-md.md)] , и для [!INCLUDE[win8](../../includes/win8-md.md)].  
  
 Альтернативой для репликации является синхронизация баз данных с помощью Microsoft Sync Framework. Sync Framework включает в себя компоненты и интуитивно понятный и гибкий API, облегчающий синхронизацию баз данных SQL Server, SQL Server Express, SQL Server Compact и SQL Azure. Sync Framework также включает в себя классы, которые можно адаптировать для синхронизации базы данных SQL Server и любой другой базы данных, совместимой с ADO.NET. Подробную документацию по компонентам синхронизации баз данных Sync Framework см. в статье [Синхронизация баз данных](https://go.microsoft.com/fwlink/?LinkId=209079). Общие сведения о платформе Sync Framework см. в [Центре разработчиков Microsoft Sync Framework](https://go.microsoft.com/fwlink/?LinkId=209078). Сравнение между Sync Framework и репликацией слиянием приведено в статье [Обзор синхронизации баз данных](https://msdn.microsoft.com/library/bb902818\(SQL.110\).aspx)  
  

## <a name="whats-new"></a>Новые возможности 
- Репликация в SQL Server 2017 не содержит существенных новых функций по сравнению с SQL Server. 
- Репликация в SQL Server 2016 не содержит существенных новых функций по сравнению с SQL Server. 

Сведения об обратной совместимости см. в разделе [Обратная совместимость репликации](replication-backward-compatibility.md). 


 ## <a name="replication-security"></a>Безопасность репликации
  
-   [Просмотр и изменение параметров безопасности репликации](security/view-and-modify-replication-security-settings.md)  
-   [Управление именами для входа в списке доступа к публикации](security/manage-logins-in-the-publication-access-list.md)  
  
## <a name="publishing-and-distribution"></a>Публикация и распространение  
  
-   [Настройка публикации и распространения](configure-publishing-and-distribution.md)   
-   [Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md)   
-   [Отключение публикации и распространения](disable-publishing-and-distribution.md)  
  
## <a name="publications-and-articles"></a>Публикации и статьи 
  
-   [Create a Publication](publish/create-a-publication.md)    
-   [Определение статьи](publish/define-an-article.md)   
-   [Просмотр и изменение свойств публикации](publish/view-and-modify-publication-properties.md)   
-   [View and Modify Article Properties (Просмотр и изменение свойств статьи)](publish/view-and-modify-article-properties.md)    
-   [Delete a Publication (Удаление публикации)](publish/delete-a-publication.md)   
-   [Delete an Article (Удаление статьи)](publish/delete-an-article.md)    
-   [Создание публикации из базы данных Oracle](publish/create-a-publication-from-an-oracle-database.md)   
-   [Set the Expiration Period for Subscriptions](publish/set-the-expiration-period-for-subscriptions.md) (Установка срока действия подписок)  
-   [Specify Schema Options (Указание параметров схемы)](publish/specify-schema-options.md)  
-   [Replicate Schema Changes (Репликация изменений схемы)](publish/replicate-schema-changes.md)    
-   [Manage Identity Columns (Управление столбцами идентификаторов)](publish/manage-identity-columns.md)   
-   [Set the Compatibility Level for Merge Publications](publish/set-the-compatibility-level-for-merge-publications.md) (Задание уровня совместимости для публикаций слиянием)  
  
### <a name="snapshot-options"></a>Параметры моментального снимка  
  
-   [Настройка свойств моментальных снимков](publish/configure-snapshot-properties-replication-transact-sql-programming.md)    
-   [Deliver a Snapshot Through FTP](publish/deliver-a-snapshot-through-ftp.md) (Доставка моментального снимка через FTP) 
  
### <a name="filter-data"></a>Фильтрация данных  
  
-   [Определение и изменение фильтра столбцов](publish/define-and-modify-a-column-filter.md)    
-   [Определение и изменение статического строкового фильтра](publish/define-and-modify-a-static-row-filter.md)    
-   [Define and Modify a Parameterized Row Filter for a Merge Article](publish/define-and-modify-a-parameterized-row-filter-for-a-merge-article.md)    
-   [Optimize Parameterized Row Filters (Оптимизация параметризованных фильтров строк)](publish/optimize-parameterized-row-filters.md)    
-   [Define and Modify a Join Filter Between Merge Articles](publish/define-and-modify-a-join-filter-between-merge-articles.md) (Определение и изменение фильтра соединения между статьями публикации слиянием)  
  
### <a name="transactional-replication-options"></a>Параметры репликации транзакций  
  
-   [Set the Propagation Method for Data Changes to Transactional Articles](publish/set-the-propagation-method-for-data-changes-to-transactional-articles.md) (Задание метода распространения изменений данных в транзакционные статьи)    
-   [Enable Updating Subscriptions for Transactional Publications](publish/enable-updating-subscriptions-for-transactional-publications.md) (Включение обновляемых подписок для публикаций транзакций)  
  
### <a name="merge-replication-options"></a>Параметры репликации слиянием  
  
-   [Определение связи логических записей между статьями таблиц слияния](publish/define-a-logical-record-relationship-between-merge-table-articles.md)    
-   [Указание свойств репликации слиянием](publish/specify-merge-replication-properties.md)    
-   [Определение арбитра для статей публикации слиянием](publish/specify-a-merge-article-resolver.md)    

  
## <a name="manage-subscriptions"></a>Управление подписками  
  
-   [Создание подписки по запросу](create-a-pull-subscription.md)    
-   [Просмотр и изменение свойств подписки по запросу](view-and-modify-pull-subscription-properties.md)    
-   [Удаление подписки по запросу](delete-a-pull-subscription.md)    
-   [Create a Push Subscription](create-a-push-subscription.md) (Создание принудительной подписки)   
-   [Просмотр и изменение свойств принудительной подписки](view-and-modify-push-subscription-properties.md)   
-   [Delete a Push Subscription](delete-a-push-subscription.md) (Удаление принудительной подписки)   
-   [Specify Synchronization Schedules](specify-synchronization-schedules.md) (Указание расписаний синхронизации)    
-   [Создание обновляемой подписки для публикации транзакций](publish/create-an-updatable-subscription-to-a-transactional-publication.md)  
-   [Создание подписки для подписчика, отличного от подписчика SQL Server](create-a-subscription-for-a-non-sql-server-subscriber.md)  
  
## <a name="synchronize-subscriptions"></a>Синхронизация подписок  
  
-   [Создание и применение исходного моментального снимка](create-and-apply-the-initial-snapshot.md)   
-   [Создание моментального снимка для публикации слиянием с параметризованными фильтрами](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md)    
-   [Инициализация транзакционной подписки из резервной копии](initialize-a-transactional-subscription-from-a-backup.md)    
-   [Инициализация подписки вручную](initialize-a-subscription-manually.md)    
-   [Синхронизация подписки по запросу](synchronize-a-pull-subscription.md)    
-   [Синхронизация принудительной подписки](synchronize-a-push-subscription.md)   
-   [Повторная инициализация подписки](reinitialize-a-subscription.md)    
-   [Выполнение скриптов во время синхронизации](execute-scripts-during-synchronization-replication-transact-sql-programming.md)    
-   [Реализация обработчика бизнес-логики для статьи публикации слиянием](implement-a-business-logic-handler-for-a-merge-article.md)  
-   [Отладка обработчика бизнес-логики (программирование репликации)](debug-a-business-logic-handler-replication-programming.md)    
-   [Управлять поведением триггеров и ограничений во время синхронизации](control-behavior-of-triggers-and-constraints-in-synchronization.md)    
-   [Реализация пользовательского арбитра конфликтов для статьи публикации слиянием](implement-a-custom-conflict-resolver-for-a-merge-article.md)  
  
## <a name="administeration"></a>Administeration 
  
-   [Работа с профилями агента репликации](agents/work-with-replication-agent-profiles.md)   
-   [Проверка данных на подписчике](validate-data-at-the-subscriber.md)    
-   [Управление секциями для публикации слиянием с параметризованными фильтрами](publish/manage-partitions-for-a-merge-publication-with-parameterized-filters.md)    
-   [Массовая загрузка данных в таблицы в публикации слиянием](bulk-load-data-into-tables-in-a-merge-publication.md)    
-   [Очистка метаданных слияния](administration/clean-up-merge-metadata-replication-transact-sql-programming.md)    
-   [Выполнить фиктивное обновление для статьи публикации слиянием](administration/perform-a-dummy-update-for-a-merge-article-replication-transact-sql-programming.md)    
-   [Просмотр реплицированных команд и другие сведения в базе данных распространителя](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [Включение скоординированного резервного копирования для репликации транзакций](administration/enable-coordinated-backups-for-transactional-replication.md)   
-   [Администрирование топологии Peer-to-Peer](administration/administer-a-peer-to-peer-topology-replication-transact-sql-programming.md)    
-   [Замораживание топологии репликации](administration/quiesce-a-replication-topology-replication-transact-sql-programming.md)    
-   [Настройка задания набора транзакций для издателя Oracle](administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)   
-   [Обновление скриптов репликации](administration/upgrade-replication-scripts-replication-transact-sql-programming.md)  
  
## <a name="monitor"></a>Монитор
  
-   [Allow Non-Administrators to Use Replication Monitor](monitor/allow-non-administrators-to-use-replication-monitor.md) (Предоставление пользователям без прав администратора разрешения на использование монитора репликации)    
-   [Наблюдение за репликацией программным образом](monitor/programmatically-monitor-replication.md)    
-   [Просмотр реплицированных команд и другие сведения в базе данных распространителя](monitor/view-replicated-commands-and-information-in-distribution-database.md)    
-   [Просмотр сведений о конфликтах для публикаций слиянием](view-conflict-information-for-merge-publications.md) 
-   [Измерение задержки и проверка правильности соединений для репликации транзакций](monitor/measure-latency-and-validate-connections-for-transactional-replication.md)  
  
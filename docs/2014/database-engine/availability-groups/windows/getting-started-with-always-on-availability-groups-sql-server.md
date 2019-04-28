---
title: Приступая к работе с группами доступности AlwaysOn (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], about
ms.assetid: 33f2f2d0-79e0-4107-9902-d67019b826aa
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 03758f4ac1a88a6ed3e704d72deb1727c30ebccb
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62814282"
---
# <a name="getting-started-with-alwayson-availability-groups-sql-server"></a>Начало работы с группами доступности AlwaysOn (SQL Server)
  В этом разделе описаны шаги настройки экземпляров [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] для поддержки [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] , а также для создания, управления и наблюдения за группой доступности.  
  
  
##  <a name="BeforeYouBegin"></a> Перед началом  
  
###  <a name="RecommendedReading"></a> Рекомендуем прочесть  
 Перед созданием первой группы доступности рекомендуется изучить следующие разделы.  
  
-   [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)  
  
-   [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)  
  
##  <a name="ConfigSI"></a> Настройка экземпляра SQL Server для поддержки групп доступности AlwaysOn  
  
||Шаг|Ссылки|  
|------|----------|-----------|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Включите [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].** Функция [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] должна быть включена на каждом экземпляре [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , который будет принимать участие в группе доступности.<br /><br /> **Предварительные условия.**  Главный компьютер должен являться узлом отказоустойчивой кластеризации Windows Server (WSFC).<br /><br /> Сведения о других условиях см. в подразделе "Предварительные условия и ограничения для экземпляров SQL Server" раздела [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).|[Включение и отключение групп доступности AlwaysOn](enable-and-disable-always-on-availability-groups-sql-server.md)|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Создание конечной точки зеркального отображения базы данных (если не указано).** Убедитесь, что в каждом экземпляре сервера существует [конечная точка зеркального отображения базы данных](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md). Экземпляр сервера использует эту конечную точку для получения соединения [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] от других экземпляров сервера.|Для определения наличия конечной точки зеркального отображения базы данных: [sys.database_mirroring_endpoints](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)<br /><br /> **Проверка подлинности Windows:** Создание конечной точки зеркального отображения базы данных с помощью различных средств.<br /><br /> [Мастер создания группы доступности](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Transact-SQL](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)<br /><br /> [SQL Server PowerShell](database-mirroring-always-on-availability-groups-powershell.md)<br /><br /> **Для проверки подлинности сертификата:** Создание конечной точки зеркального отображения, с помощью базы данных <br />                    [Transact-SQL](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)|  
  
##  <a name="ConfigAG"></a> Creating and Configuring a New Availability Group  
  
||Шаг|Ссылки|  
|------|----------|-----------|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Создайте группу доступности.** Создание группы доступности на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , содержащем базы данных, которые необходимо добавить к группе доступности.<br /><br /> Как минимум, создайте первоначальную первичную реплику на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором будет создана группа доступности. Можно задать от 1 до 4 вторичных реплик. Сведения о свойствах группы доступности и реплики см. в разделе [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql).<br /><br /> Настоятельно рекомендуется создать [прослушиватель группы доступности](../../listeners-client-connectivity-application-failover.md).<br /><br /> **Предварительные условия.**  Экземпляры [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на которых размещаются реплики доступности для данной группы доступности, должны размещаться на отдельных узлах одного WSFC-кластера. Единственное исключение состоит в том, что при переносе в другой кластер WSFC группа доступности может временно находится в двух кластерах.<br /><br /> Сведения о других условиях см. в подразделах "Обязательные условия и ограничения для группы доступности", "Обязательные условия и ограничения для базы данных доступности" и "Предварительные условия и ограничения для экземпляров SQL Server" раздела [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](prereqs-restrictions-recommendations-always-on-availability.md).|Для создания группы доступности можно воспользоваться следующими средствами.<br /><br /> [Мастер создания группы доступности](use-the-availability-group-wizard-sql-server-management-studio.md)<br /><br /> [Transact-SQL](create-an-availability-group-transact-sql.md)<br /><br /> [SQL Server PowerShell](create-an-availability-group-transact-sql.md)|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Присоединение дополнительных реплик к группе доступности.** Подключитесь ко всем экземплярам [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] , на которых размещена вторичная реплика, и присоедините локальную вторичную реплику к группе доступности.|[Присоединение вторичной реплики к группе доступности](join-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> Совет. При использовании мастера создания групп доступности этот этап выполняется автоматически.|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Подготовка баз данных-получателей.** На всех экземплярах сервера, где размещена вторичная реплика, восстановите резервные копии базы данных-источника с помощью инструкции RESTORE WITH NORECOVERY.|[Подготовка базы данных-получателя вручную](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)<br /><br /> Совет. Мастер создания группы доступности можно подготовить базы данных-получатели для вас. Дополнительные сведения см. в подразделе "Предварительные условия для использования полной начальной синхронизации данных" раздела [Выбор страницы начальной синхронизации данных (мастера группы доступности AlwaysOn)](select-initial-data-synchronization-page-always-on-availability-group-wizards.md).|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Присоедините базы данных-получатели к группе доступности.** На каждом экземпляре сервера, размещающем вторичную реплику, присоедините все локальные базы данных-получатели к группе доступности. При присоединении группы доступности эта база данных-получатель инициирует синхронизацию данных с соответствующей базой данных-источником.|[Присоединение базы данных-получателя к группе доступности](join-a-secondary-database-to-an-availability-group-sql-server.md)<br /><br /> Совет. Мастер создания группы доступности может выполнить этот шаг, если в каждой вторичной реплике существует каждая база данных.|  
||**Создание прослушивателя группы доступности.**  Этот шаг обязателен, если прослушиватель группы доступности еще не был создан при создании группы доступности.|[Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Передайте имя узла DNS для прослушивателя разработчикам приложений.**  Им необходимо указать это имя в строке подключения, которая будет использоваться для запроса прямого подключения к прослушивателю группы доступности. Дополнительные сведения см. в разделе [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md).|«Дальнейшие действия: Действия после создания прослушивателя группы доступности" раздела [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)|  
|![Флажок](../../media/checkboxemptycenterxtraspacetopandright.gif "Флажок")|**Настройка места выполнения заданий резервного копирования.**  Если нужно выполнить резервное копирование баз данных-получателей, то необходимо создать скрипт задания резервного копирования, который учитывает автоматический выбор при создании резервной копии. Создайте скрипт для каждой базы данных в группе доступности на каждом экземпляре сервера, на котором размещена реплика доступности для этой группы доступности.|«Дальнейшие действия: После настройки резервного копирования во вторичных репликах" раздела [Настройка резервного копирования в репликах доступности (SQL Server)](configure-backup-on-availability-replicas-sql-server.md).|  
  
##  <a name="ManageAGsEtc"></a> Managing Availability Groups, Replicas, and Databases  
  
> [!NOTE]  
>  Сведения о свойствах группы доступности и реплики см. в разделе [CREATE AVAILABILITY GROUP (Transact-SQL)](/sql/t-sql/statements/create-availability-group-transact-sql).  
  
 Управление существующими группами доступности содержит одну или несколько следующих задач.  
  
|Задача|Ссылка|  
|----------|----------|  
|Изменение [гибкой политики отработки отказа](flexible-automatic-failover-policy-availability-group.md) группы доступности для управления условиями, вызвавшими автоматический переход на другой ресурс. Эта политика актуальна, только если возможна автоматическая отработка отказа.|[Настройка гибкой политики отработки отказа группы доступности](configure-flexible-automatic-failover-policy.md)|  
|Выполнение запланированного перехода на другой ресурс вручную или принудительный переход на другой ресурс вручную (с возможной потерей данных), который обычно называется *принудительная отработка отказа*. Дополнительные сведения см. в статье [Отработка отказа и режимы отработки отказа (группы доступности AlwaysOn)](failover-and-failover-modes-always-on-availability-groups.md).|[Выполнение запланированного перехода на другой ресурс вручную](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)<br /><br /> [Выполнение принудительного перехода на другой ресурс вручную](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)|  
|Используйте стандартный набор политик для просмотра работоспособности группы доступности, ее реплик и баз данных.|[Использование управления на основе политик для просмотра работоспособности группы доступности](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)<br /><br /> [Использование панели мониторинга групп AlwaysOn](use-the-always-on-dashboard-sql-server-management-studio.md)|  
|Добавление или удаление вторичной реплики.|[Добавление вторичной реплики](add-a-secondary-replica-to-an-availability-group-sql-server.md)<br /><br /> [Удаление вторичной реплики](remove-a-secondary-replica-from-an-availability-group-sql-server.md)|  
|Приостановка или возобновление базы данных доступности. Во время приостановки базы данных-получателя, она сохраняется в текущем состоянии, пока ее работа не будет возобновлена.|[Приостановка базы данных](suspend-an-availability-database-sql-server.md)<br /><br /> [Возобновление базы данных](resume-an-availability-database-sql-server.md)|  
|Добавление или удаление базы данных.|[Добавление базы данных](availability-group-add-a-database.md)<br /><br /> [Удаление базы данных-получателя](remove-a-secondary-database-from-an-availability-group-sql-server.md)<br /><br /> [Удаление базы данных-источника](remove-a-primary-database-from-an-availability-group-sql-server.md)|  
|Создание или повторная настройка прослушивателя группы доступности.|[Создание или настройка прослушивателя группы доступности](create-or-configure-an-availability-group-listener-sql-server.md)|  
|Удаление группы доступности.|[Удаление группы доступности](remove-an-availability-group-sql-server.md)|  
|Устранение неполадок с операциями добавления файла. Такая операция может потребоваться, если база данных-источник и база данных-получатель имеют различные пути к файлу.|[Устранение неполадок с операцией добавления файлов, давшей сбой](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)|  
|Изменение свойств реплики доступности.|[Изменение режима доступности](change-the-availability-mode-of-an-availability-replica-sql-server.md)<br /><br /> [Изменение режима отработки отказа](change-the-failover-mode-of-an-availability-replica-sql-server.md)<br /><br /> [Настройка приоритета резервного копирования (и предпочтений автоматического резервного копирования)](configure-backup-on-availability-replicas-sql-server.md)<br /><br /> [Настройка доступа только для чтения](configure-read-only-access-on-an-availability-replica-sql-server.md)<br /><br /> [Настройка маршрутизации только для чтения](configure-read-only-routing-for-an-availability-group-sql-server.md)<br /><br /> [Изменение периода времени ожидания сеанса](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)|  
  
##  <a name="MonitorAGsEtc"></a> Monitoring Availability Groups  
 Для отслеживания свойств и состояния группы доступности AlwaysOn можно пользоваться следующими средствами.  
  
|Инструмент|Краткое описание|Ссылки|  
|----------|-----------------------|-----------|  
|Пакет мониторинга System Center для SQL Server|Пакет мониторинга для SQL Server (SQLMP) является рекомендованным решением для мониторинга групп доступности, реплик доступности и баз данных доступности для ИТ-администраторов. Для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] особенно релевантны следующие функции мониторинга.<br /><br /> Автоматическое обнаружение групп доступности, реплик доступности и баз данных доступности среди сотен компьютеров. Это позволяет легко отслеживать всю номенклатуру [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .<br /><br /> Полнофункциональная рассылка уведомлений и бронирование в System Center Operations Manager (SCOM). Эти функции обеспечивают подробный набор знаний о том, как быстрее решить проблему.<br /><br /> В пользовательском расширении мониторинга исправности AlwaysOn используется управление на основе политик (PBM).<br /><br /> Производится свертка исправности с баз данных доступности до реплик доступности.<br /><br /> Пользовательские задачи, которые управляют [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] из консоли System Center Operations Manager.|Чтобы загрузить пакет мониторинга (SQLServerMP.msi) и *Руководство по пакету управления SQL Server для System Center Operations Manager* (SQLServerMPGuide.doc), перейдите на страницу:<br /><br /> [Пакет мониторинга System Center для SQL Server](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и динамические административные представления предоставляют широкий набор сведений о группах доступности и их репликах, базах данных, прослушивателях и кластерной среде WSFC.|[Отслеживание групп доступности (Transact-SQL)](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Область **Сведения обозревателя объектов** содержит базовые сведения о группах доступности, размещенных на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым установлено соединение.<br /><br /> Совет. Эта панель используется для выбора нескольких групп доступности, реплик или баз данных и выполнения рутинных задач администрирования с выбранными объектами; Например удаления нескольких реплик доступности или баз данных из группы доступности.|[Использование области «Сведения обозревателя объектов» для отслеживания групп доступности](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Диалоговые окна**Свойства** позволяют просматривать свойства групп доступности, реплик или прослушивателей, а также, в некоторых случаях, позволяют изменять значения данных свойств.|[Свойства группы доступности](view-availability-group-properties-sql-server.md)<br /><br /> [Свойства реплики доступности](view-availability-replica-properties-sql-server.md)<br /><br /> [Свойства прослушивателя группы доступности](view-availability-group-listener-properties-sql-server.md)|  
|Системный монитор|Объект производительности **SQLServer:Availability Replica** содержит счетчики производительности, которые сообщают сведения о репликах доступности.|[SQL Server, реплика доступности](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|Системный монитор|Объект производительности **SQLServer:Database Replica** содержит счетчики производительности, которые сообщают сведения о базах данных-получателях для определенной вторичной реплики.<br /><br /> Объект **SQLServer:Databases** в SQL Server содержит счетчики производительности, которые, среди прочего, отслеживают активность журнала транзакций. Следующие счетчики имеют особое значение для отслеживания активности журнала транзакций для баз данных доступности: **Время записи журнала на диск (мс)**, **Записей журнала на диск/с**, **Неудачных обращений к кэшу пула журнала/с**, **Операций чтения диска пула журнала/с** и **Запросов пула журнала/с**.|[SQL Server, реплика базы данных](../../../relational-databases/performance-monitor/sql-server-database-replica.md)<br /><br /> [SQL Server, объект Databases](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Видео — введение в AlwaysOn.**  [Серия Microsoft SQL Server с кодовым названием «Denali» AlwaysOn, часть 1: представляем решение высокого уровня доступности следующего поколения](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
-   **Видео A глубокое погружение в AlwaysOn:**  [Серия Microsoft SQL Server с кодовым названием «Denali» AlwaysOn, часть 2: Создание решения критически важных высокого уровня доступности с помощью AlwaysOn](http://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   **Технический документ:**  [Microsoft SQL Server AlwaysOn Solutions Guide for высокий уровень доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   **Блоги**  [Блог группы AlwaysOn SQL Server: Официальный блог по SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a>См. также  
 [Группы доступности AlwaysOn &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md)   
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Настройка экземпляра сервера для групп доступности AlwaysOn &#40;SQL Server&#41;](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)   
 [Создание и настройка групп доступности (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md)   
 [Отслеживание групп доступности (SQL Server)](monitoring-of-availability-groups-sql-server.md)   
 [Общие сведения об инструкциях Transact-SQL для групп доступности AlwaysOn &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md)   
 [Обзор командлетов PowerShell для групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
  

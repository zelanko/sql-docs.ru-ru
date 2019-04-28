---
title: Отслеживание групп доступности (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 1d5e3291-0d0a-45a1-88e5-1fc242d17210
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1793032a72ae1dd150caa5ddd1739f7f5620bce1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790200"
---
# <a name="monitoring-of-availability-groups-sql-server"></a>Отслеживание групп доступности (SQL Server)
  Для отслеживания свойств и состояния группы доступности AlwaysOn можно пользоваться следующими средствами.  
  
|Инструмент|Краткое описание|Ссылки|  
|----------|-----------------------|-----------|  
|Пакет мониторинга System Center для SQL Server|Пакет мониторинга для SQL Server (SQLMP) является рекомендованным решением для мониторинга групп доступности, реплик доступности и баз данных доступности для ИТ-администраторов. Для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] особенно релевантны следующие функции мониторинга.<br /><br /> Автоматическое обнаружение групп доступности, реплик доступности и баз данных доступности среди сотен компьютеров. Это позволяет легко отслеживать всю номенклатуру [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] .<br /><br /> Полнофункциональная рассылка уведомлений и бронирование в System Center Operations Manager (SCOM). Эти функции обеспечивают подробный набор знаний о том, как быстрее решить проблему.<br /><br /> В пользовательском расширении мониторинга исправности AlwaysOn используется управление на основе политик (PBM).<br /><br /> Производится свертка исправности с баз данных доступности до реплик доступности.<br /><br /> Пользовательские задачи, которые управляют [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] из консоли System Center Operations Manager.|Чтобы загрузить пакет мониторинга (SQLServerMP.msi) и *Руководство по пакету управления SQL Server для System Center Operations Manager* (SQLServerMPGuide.doc), перейдите на страницу:<br /><br /> [Пакет мониторинга System Center для SQL Server](https://www.microsoft.com/download/details.aspx?displaylang=en&id=10631)|  
|[!INCLUDE[tsql](../../../includes/tsql-md.md)]|[!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] и динамические административные представления предоставляют широкий набор сведений о группах доступности и их репликах, базах данных, прослушивателях и кластерной среде WSFC.|[Отслеживание групп доступности (Transact-SQL)](monitor-availability-groups-transact-sql.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Область **Сведения обозревателя объектов** содержит базовые сведения о группах доступности, размещенных на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , с которым установлено соединение.<br /><br /> Совет. Эта панель используется для выбора нескольких групп доступности, реплик или баз данных и выполнения рутинных задач администрирования с выбранными объектами; Например удаления нескольких реплик доступности или баз данных из группы доступности.|[Использование сведений обозревателя объектов для мониторинга групп доступности (среда SQL Server Management Studio)](use-object-explorer-details-to-monitor-availability-groups.md)|  
|[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]|Диалоговые окна**Свойства** позволяют просматривать свойства групп доступности, реплик или прослушивателей, а также, в некоторых случаях, позволяют изменять значения данных свойств.|[Просмотр свойств группы доступности (SQL Server)](view-availability-group-properties-sql-server.md)<br /><br /> [Просмотр свойств реплики доступности (SQL Server)](view-availability-replica-properties-sql-server.md)<br /><br /> [Просмотр свойств прослушивателя группы доступности (SQL Server)](view-availability-group-listener-properties-sql-server.md)|  
|Системный монитор|Объект производительности **SQLServer:Availability Replica** содержит счетчики производительности, которые сообщают сведения о репликах доступности.|[SQL Server, реплика доступности](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)|  
|Системный монитор|Объект производительности **SQLServer:Database Replica** содержит счетчики производительности, которые сообщают сведения о базах данных-получателях для определенной вторичной реплики.<br /><br /> Объект **SQLServer:Databases** в SQL Server содержит счетчики производительности, которые, среди прочего, отслеживают активность журнала транзакций. Следующие счетчики имеют особое значение для отслеживания активности журнала транзакций для баз данных доступности: **Время записи журнала на диск (мс)**, **Записей журнала на диск/с**, **Неудачных обращений к кэшу пула журнала/с**, **Операций чтения диска пула журнала/с** и **Запросов пула журнала/с**.|[SQL Server, реплика базы данных](../../../relational-databases/performance-monitor/sql-server-database-replica.md) и [SQL Server, объект баз данных](../../../relational-databases/performance-monitor/sql-server-databases-object.md)|  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [AlwaysOn работоспособности модель, часть 1 архитектура модели исправности](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/09/overview-of-the-alwayson-manageability-health-model.aspx)  
  
     [Модель исправности AlwaysOn часть 2 — расширение модели исправности](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/extending-the-alwayson-health-model.aspx)  
  
     [Отслеживание работоспособности AlwaysOn с помощью PowerShell, часть 1. Общие сведения о командлетах](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-1.aspx)  
  
     [Отслеживание работоспособности AlwaysOn с помощью PowerShell, часть 2: Расширенное использование командлетов](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/13/monitoring-alwayson-health-with-powershell-part-2.aspx)  
  
     [Отслеживание работоспособности AlwaysOn с помощью PowerShell, часть 3. Простое приложение для мониторинга](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/monitoring-alwayson-health-with-powershell-part-3.aspx)  
  
     [Отслеживание работоспособности AlwaysOn с помощью PowerShell, часть 4. Интеграция с агентом SQL Server](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/15/the-always-on-health-model-part-4.aspx)  
  
     [Блоги группы AlwaysOn SQL Server: Официальный блог по SQL Server AlwaysOn Team](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги инженеров CSS SQL Server](https://blogs.msdn.com/b/psssql/)  
  
-   **Технические документы:**  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также  
 [Представления каталога групп доступности AlwaysOn &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/always-on-availability-groups-catalog-views-transact-sql)   
 [Динамические административные представления и функции групп доступности AlwaysOn &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/always-on-availability-groups-dynamic-management-views-functions)   
 [Гибкая политика отработки отказа для автоматического перехода на другой ресурс группы доступности (SQL Server)](flexible-automatic-failover-policy-availability-group.md)   
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Автоматическое восстановление страниц &#40;для групп доступности и зеркального отображения базы данных&#41;](../../../sql-server/failover-clusters/automatic-page-repair-availability-groups-database-mirroring.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  

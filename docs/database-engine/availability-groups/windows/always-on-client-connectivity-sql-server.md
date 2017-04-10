---
title: "Подключение клиента AlwaysOn (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "группы доступности [SQL Server], прослушиватели"
  - "Группы доступности [SQL Server], требования и ограничения"
  - "группы доступности [SQL Server], подключение клиента"
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
caps.latest.revision: 22
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 21
---
# Подключение клиента AlwaysOn (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе обсуждаются особенности обеспечения подключений клиентов к группам доступности AlwaysOn, в том числе предварительные условия, ограничения и рекомендации по конфигурации и настройке клиентов.  
  
 **В этом разделе.**  
  
-   [Поддержка возможности подключения клиента](#ClientConnSupport)  
  
-   [Связанные задачи](#RelatedTasks)  
  
##  <a name="ClientConnSupport"></a> Поддержка возможности подключения клиента  
 В приведенном далее разделе представлены сведения о поддержке [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для обмена данными с клиентом.  
  
 **Поддержка драйверов**  
  
 В следующей таблице приведены сведения о поддержке драйверов для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
|Драйвер|Отработка отказа с использованием нескольких подсетей|Назначение приложения|Маршрутизация только для чтения|Переход на другой ресурс с использованием нескольких подсетей: переход на другой ресурс для конечной точки одной более быстрой подсети|Переход на другой ресурс с использованием нескольких подсетей: разрешение именованного экземпляра для кластеризованных экземпляров SQL|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Да|Да|Да|Да|Да|  
|SQL Native Client 11.0 OLEDB|Нет|Да|Да|Нет|Нет|  
|ADO.NET с платформой .NET Framework 4.0 с улучшением подключения*|Да|Да|Да|Да|Да|  
|ADO.NET с платформой .NET Framework 3.5 с пакетом обновления 1 (SP1) с улучшением подключения**|Да|Да|Да|Да|Да|  
|Драйвер Microsoft JDBC 4.0 для SQL Server|Да|Да|Да|Да|Да|  
  
 * Скачайте исправление для улучшения подключения для ADO .NET с платформой .NET Framework 4.0: [http://support.microsoft.com/kb/2600211](http://support.microsoft.com/kb/2600211).  
  
 ** Скачайте исправление для улучшения подключения для ADO .NET с платформой .NET Framework 3.5 с пакетом обновления 1 (SP1): [http://support.microsoft.com/kb/2654347](http://support.microsoft.com/kb/2654347).  
  
> [!IMPORTANT]  
>  Для подключения к прослушивателю группы доступности клиент должен использовать строку подключения TCP.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание и настройка групп доступности (SQL Server)](../../../database-engine/availability-groups/windows/creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server.md)  
  
## См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Отказоустойчивая кластеризация и группы доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/prereqs, restrictions, recommendations - always on availability.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../../database-engine/availability-groups/windows/listeners, client connectivity, application failover.md)   
 [Сведения о доступе клиентского подключения к репликам доступности (SQL Server)](../../../database-engine/availability-groups/windows/about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Руководство по решениям режима AlwaysOn в Microsoft SQL Server для обеспечения высокой доступности и аварийного восстановления](http://go.microsoft.com/fwlink/?LinkId=227600)   
 [Блоги команды разработчиков SQL Server AlwaysOn: официальный блог по SQL Server AlwaysOn](http://blogs.msdn.com/b/sqlAlways%20On/)   
 [На компьютерах под управлением Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 или Windows Server 2008 R2 происходит долговременная задержка при повторном подключении с помощью протокола IPSec](http://support.microsoft.com/kb/980915)   
 [Службе кластера необходимо около 30 секунд для отработки отказа IP-адресов IPv6 в Windows Server 2008 R2](http://support.microsoft.com/kb/2578113)   
 [Медленная отработка отказа при отсутствии маршрутизатора между кластером и сервером приложений](http://support.microsoft.com/kb/2582281)  
  
  
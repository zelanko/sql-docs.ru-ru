---
title: Подключение клиента AlwaysOn (SQL Server) | Документы Майкрософт
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], listeners
- Availability Groups [SQL Server], prerequisites and restrictions
- Availability Groups [SQL Server], client connectivity
ms.assetid: b456448d-1757-48c8-8bbb-2d1c2d6d61e9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 53f514e83e980e0a91184581d186bcb4046727c3
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48192752"
---
# <a name="always-on-client-connectivity-sql-server"></a>Подключение клиента AlwaysOn (SQL Server)
  В этом разделе обсуждаются особенности обеспечения подключений клиентов к группам доступности AlwaysOn, в том числе предварительные условия, ограничения и рекомендации по конфигурации и настройке клиентов.  
  
 
  
##  <a name="ClientConnSupport"></a> Поддержка возможности подключения клиента  
 В приведенном далее разделе представлены сведения о поддержке [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для обмена данными с клиентом.  
  
 **Поддержка драйверов**  
  
 В следующей таблице приведены сведения о поддержке драйверов для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
|Драйвер|Отработка отказа с использованием нескольких подсетей|Назначение приложения|Маршрутизация только для чтения|Переход на другой ресурс с использованием нескольких подсетей: переход на другой ресурс для конечной точки одной более быстрой подсети|Переход на другой ресурс с использованием нескольких подсетей: разрешение именованного экземпляра для кластеризованных экземпляров SQL|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Да|Да|Да|Да|Да|  
|SQL Native Client 11.0 OLEDB|Нет|Да|Да|Нет|Нет|  
|ADO.NET с платформой .NET Framework 4.0 с улучшением подключения**<sup>*</sup>**|Да|Да|Да|Да|Да|  
|ADO.NET с .NET Framework 3.5 SP1 с улучшением подключения **<sup>**</sup>**|Да|Да|Да|Да|Да|  
|Драйвер Microsoft JDBC 4.0 для SQL Server|Да|Да|Да|Да|Да|  
  
 **<sup>*</sup>**  Скачайте исправление подключения для ADO .NET с платформой .NET Framework 4.0: [ http://support.microsoft.com/kb/2600211 ](http://support.microsoft.com/kb/2600211).  
  
 **<sup>**</sup>** Скачайте исправление подключения для ADO.NET с .NET Framework 3.5 с пакетом обновления 1: [ http://support.microsoft.com/kb/2654347 ](http://support.microsoft.com/kb/2654347).  
  
> [!IMPORTANT]  
>  Для подключения к прослушивателю группы доступности клиент должен использовать строку подключения TCP.  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание и настройка групп доступности (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a>См. также  
 [Обзор групп доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Отказоустойчивая кластеризация и группы доступности AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для групп доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md)   
 [Сведения о доступе клиентского подключения к репликам доступности (SQL Server)](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Microsoft SQL Server AlwaysOn Solutions Guide for высокий уровень доступности и аварийного восстановления](http://go.microsoft.com/fwlink/?LinkId=227600)   
 [Блог группы AlwaysOn SQL Server: Официальный блог SQL Server AlwaysOn Team](http://blogs.msdn.com/b/sqlalwayson/)   
 [На компьютерах под управлением Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 или Windows Server 2008 R2 происходит долговременная задержка при повторном подключении с помощью протокола IPSec](http://support.microsoft.com/kb/980915)   
 [Службе кластера необходимо около 30 секунд для отработки отказа IP-адресов IPv6 в Windows Server 2008 R2](http://support.microsoft.com/kb/2578113)   
 [Медленная отработка отказа при отсутствии маршрутизатора между кластером и сервером приложений](http://support.microsoft.com/kb/2582281)  
  
  

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
ms.openlocfilehash: 446a0f709c35028efd5a39b347919b1e0b40b4b4
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/17/2020
ms.locfileid: "84937182"
---
# <a name="always-on-client-connectivity-sql-server"></a>Подключение клиента AlwaysOn (SQL Server)
  В этом разделе обсуждаются особенности обеспечения подключений клиентов к группам доступности AlwaysOn, в том числе предварительные условия, ограничения и рекомендации по конфигурации и настройке клиентов.  
  
 
  
##  <a name="client-connectivity-support"></a><a name="ClientConnSupport"></a>Поддержка подключения клиентов  
 В приведенном далее разделе представлены сведения о поддержке [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] для обмена данными с клиентом.  
  
 **Поддержка драйверов**  
  
 В следующей таблице приведены сведения о поддержке драйверов для [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].  
  
|Драйвер|Отработка отказа с использованием нескольких подсетей|Назначение приложения|Маршрутизация только для чтения|Отработка отказа в нескольких подсетях: ускоряет отработку отказа конечной точки одной подсети|Отработка отказа в нескольких подсетях: разрешение именованного экземпляра для кластеризованных экземпляров SQL|  
|------------|----------------------------|------------------------|------------------------|--------------------------------------------------------------------|-----------------------------------------------------------------------------------|  
|SQL Native Client 11.0 ODBC|Да|Да|Да|Да|Да|  
|SQL Native Client 11.0 OLEDB|нет|Да|Да|Нет|нет|  
|ADO.NET с .NET Framework 4,0 с исправлением подключения**<sup>*</sup>** |Да|Да|Да|Да|Да|  
|ADO.NET с .NET Framework 3,5 с пакетом обновления 1 (SP1) с исправлением подключения**<sup>**</sup>** |Да|Да|Да|Да|Да|  
|Драйвер Microsoft JDBC 4.0 для SQL Server|Да|Да|Да|Да|Да|  
  
 **<sup>*</sup>** Скачайте Исправление подключения для ADO .NET с .NET Framework 4,0: [https://support.microsoft.com/kb/2600211](https://support.microsoft.com/kb/2600211) .  
  
 **<sup>**</sup>* * Загрузите исправление подключения для ADO.NET с .NET Framework 3,5 с пакетом обновления 1 (SP1): [https://support.microsoft.com/kb/2654347](https://support.microsoft.com/kb/2654347) .  
  
> [!IMPORTANT]  
>  Для подключения к прослушивателю группы доступности клиент должен использовать строку подключения TCP.  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Связанные задачи  
  
-   [Создание и настройка групп доступности (SQL Server)](creation-and-configuration-of-availability-groups-sql-server.md)  
  
-   [Создание или настройка прослушивателя группы доступности (SQL Server)](create-or-configure-an-availability-group-listener-sql-server.md)  
  

  
## <a name="see-also"></a>См. также:  
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Отказоустойчивая кластеризация и группы доступности AlwaysOn &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md)   
 [Предварительные требования, ограничения и рекомендации для группы доступности AlwaysOn &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)   
 [Прослушиватели групп доступности, возможность подключения клиентов и отработка отказа приложений (SQL Server)](../../listeners-client-connectivity-application-failover.md)   
 [Сведения о доступе клиентского подключения к репликам доступности (SQL Server)](about-client-connection-access-to-availability-replicas-sql-server.md)   
 [Microsoft SQL Server рекомендации по решениям AlwaysOn для обеспечения высокого уровня доступности и аварийного восстановления](https://go.microsoft.com/fwlink/?LinkId=227600)   
 [Блог группы SQL Server AlwaysOn: Официальный блог группы SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)   
 [При повторном подключении подключения IPSec с компьютера под управлением Windows Server 2003, Windows Vista, Windows Server 2008, Windows 7 или Windows Server 2008 R2 возникает длительная задержка](https://support.microsoft.com/kb/980915)   
 [служба кластеров занимает около 30 секунд для отработки отказа IP-адресов IPv6 в Windows Server 2008 R2](https://support.microsoft.com/kb/2578113)   
 [Медленная отработка отказа при отсутствии маршрутизатора между кластером и сервером приложений](https://support.microsoft.com/kb/2582281)  
  
  

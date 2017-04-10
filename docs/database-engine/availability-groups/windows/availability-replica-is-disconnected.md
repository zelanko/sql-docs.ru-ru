---
title: "Реплика доступности отключена | Microsoft Docs"
ms.custom: ""
ms.date: "05/17/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.swb.agdashboard.arp2connected.issues.f1"
helpviewer_keywords: 
  - "группы доступности [SQL Server], политики"
ms.assetid: 1a2162d3-54fb-4356-b349-effbdc15a5a4
caps.latest.revision: 12
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 12
---
# Реплика доступности отключена
    
## Введение  
  
|||  
|-|-|  
|**Имя политики**|Состояние соединения с репликами доступности|  
|**Проблема**|Реплика доступности отключена.|  
|**Категория**|**Критическая**|  
|**Аспект**|Реплика доступности|  
  
## Описание  
 Эта политика проверяет состояние соединения между репликами доступности. Эта политика находится в нерабочем состоянии, если подключение к реплике доступности имеет состояние DISCONNECTED. В остальном политика находится в рабочем состоянии.  
  
> [!NOTE]  
>  Для этого выпуска [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] сведения о возможных причинах проблем и решениях доступны в разделе [Реплика доступности отключена](http://go.microsoft.com/fwlink/p/?LinkId=220857) в TechNet Wiki.  
  
## Возможные причины  
 Вторичная реплика не подключена к первичной реплике. Состояние соединения — DISCONNECTED. Возможны следующие причины этой проблемы.  
  
-   Порт подключения может конфликтовать с другим приложением.  
  
-   Несоответствие типа или алгоритма шифрования.  
  
-   Конечная точка подключения была удалена или не была запущена.  
  
-   Транспорт отключен.  
  
## Возможные решения  
 Ниже перечислены возможные решения этой проблемы:  
  
-   Проверьте конфигурацию конечной точки зеркального отображения базы данных для экземпляров первичной и вторичной реплики и обновите конфигурацию с несоответствием.  
  
-   Проверьте наличие конфликта портов и при его обнаружении измените номер порта.  
  
## См. также:  
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Использование панели мониторинга AlwaysOn (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
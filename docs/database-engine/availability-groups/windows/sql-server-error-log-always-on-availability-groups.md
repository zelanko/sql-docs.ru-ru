---
title: Журнал ошибок SQL Server (группы доступности)
description: Сведения о событиях журнала ошибок SQL Server, влияющих на группу доступности Always On, и о симптомах, которые должны привести к проверке журнала ошибок.
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 39d0c98d-75af-4dd1-b908-30d31af56f2a
author: rothja
ms.author: jroth
ms.openlocfilehash: 4c44f65761fcb54d8ad9b8eac0fc5e02bce82181
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2020
ms.locfileid: "85898069"
---
# <a name="sql-server-error-log-always-on-availability-groups"></a>Журнал ошибок SQL Server (группы доступности AlwaysOn)
[!INCLUDE [SQL Server](../../../includes/applies-to-version/sqlserver.md)]
  Журнал ошибок SQL Server содержит события, затрагивающие группы доступности AlwaysOn, например:  
  
-   Взаимодействие с кластером отказоустойчивой кластеризации Windows Server (WSFC)    
-   Переходы состояния для реплик доступности    
-   Переходы состояния для баз данных доступности    
-   Состояние подключения для баз данных доступности между первичными и вторичными репликами    
-   Состояния для конечных точек групп доступности    
-   Состояния для прослушивателей групп доступности    
-   Состояние аренды между библиотекой ресурсов SQL Server (выполняемой в кластере WSFC) и экземпляром SQL Server (дополнительные сведения см. в разделе [Принцип работы. Время ожидания аренды Always On в SQL Server](https://blogs.msdn.com/b/psssql/archive/2012/09/07/how-it-works-sql-server-alwayson-lease-timeout.aspx))    
-   События ошибок в группе доступности  

При наличии следующих симптомов нужно изучить журнал ошибок SQL Server:  

-   Не удается обратиться к базам данных доступности    
-   Непредвиденный переход на другой ресурс для группы доступности    
-   Непредвиденный переход группы доступности в состояние разрешения    
-   Группа доступности в неопределенном состоянии  
  
Дополнительные сведения см. в разделе [Просмотр журнала ошибок SQL Server (среда SQL Server Management Studio)](~/relational-databases/performance/view-the-sql-server-error-log-sql-server-management-studio.md).  
  
  

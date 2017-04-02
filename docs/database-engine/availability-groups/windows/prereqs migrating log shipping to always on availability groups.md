---
title: "Необходимые условия для перехода от использования доставки журналов к использованию групп доступности AlwaysOn (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/23/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-high-availability"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "доставка журналов [SQL Server], группы доступности AlwaysOn"
  - "Группы доступности [SQL Server], взаимодействие"
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
caps.latest.revision: 24
ms.author: "mikeray"
manager: "jhubbard"
---
# Необходимые условия для перехода от использования доставки журналов к использованию групп доступности AlwaysOn (SQL Server)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  В этом разделе описаны предварительные условия для преобразования базы данных-источника доставки журналов вместе с одной или несколькими базами данных-получателями в базу данных-источник и базы данных-получатели AlwaysOn.  
  
> [!NOTE]  
>  В качестве первичной базы данных для доставки журналов вы можете настроить любую базу данных-источник или базу данных-получатель (по возможности предназначенную для чтения).  
  
 **В этом разделе:**  
  
-   [Предварительные условия для группы доступности](#AGPrereqsRealAddress)  
  
-   [Предварительные условия для доставки журналов](#LogShipPrereqs)  
  
-   [Связанные задачи](#RelatedTasks)  
  
-   [См. также](#RelatedContent)  
  
##  <a name="AGPrereqsRealAddress"></a> Предварительные условия для группы доступности  
 Чтобы разрешить выполнение заданий резервного копирования в первичной реплике группы доступности, используйте следующие параметры резервного копирования групп доступности AlwaysOn:  
  
|Свойство|Настройка|  
|--------------|-------------|  
|Автоматическое резервное копирование группы доступности|Только в первичной реплике|  
|Приоритет резервного копирования первичной реплики.|>0|  
  
 **Дополнительные сведения см. в следующих разделах:**  
  
 [Просмотр свойств группы доступности (SQL Server)](../../../database-engine/availability-groups/windows/view-availability-group-properties-sql-server.md)  
  
 [Настройка резервного копирования в репликах доступности (SQL Server)](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="LogShipPrereqs"></a> Предварительные условия для доставки журналов  
  
-   База данных-источник доставки журналов должна находиться на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], на котором размещается первоначальная или текущая первичная реплика группы доступности.  
  
-   Для преобразования базы данных-получателя доставки журналов в базу данных-получатель AlwaysOn необходимо:  
  
    -   использовать то же имя, что и у базы данных-источника.  
  
    -   Размещение на экземпляре сервера, на котором размещается вторичная реплика для группы доступности.  
  
 После выполнения задания резервного копирования для базы данных-источника отключите задание резервного копирования и после выполнения задания по восстановлению для выбранной базы данных-получателя отключите задание восстановления.  
  
 После создания всех баз данных-получателей для группы доступности при необходимости проведения резервного копирования во вторичных репликах нужно изменить параметры автоматического резервного копирования для группы доступности.  
  
 **Дополнительные сведения см. в следующих разделах:**  
  
 [Преобразование конфигурации доставки журналов в группу доступности](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (блог по SQL Server)  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **доставка журналов;**  
  
-   [Обновление доставки журналов до SQL Server 2016 (Transact-SQL)](../../../database-engine/log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Удаление доставки журналов (SQL Server)](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
 **Группы доступности AlwaysOn**  
  
-   [Использование мастера групп доступности (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Использование диалогового окна "Создание группы доступности" (среда SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Создание группы доступности (Transact-SQL)](../../../database-engine/availability-groups/windows/create-an-availability-group-transact-sql.md)  
  
-   [Создание группы доступности (SQL Server PowerShell)](../../../database-engine/availability-groups/windows/create-an-availability-group-sql-server-powershell.md)  
  
-   [Присоединение базы данных-получателя к группе доступности (SQL Server)](../../../database-engine/availability-groups/windows/join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Настройка резервного копирования в репликах доступности (SQL Server)](../../../database-engine/availability-groups/windows/configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Блоги**  
  
     [Преобразование конфигурации доставки журналов в группу доступности](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx)  
  
     [Добавление базы данных-источника доставки журналов и баз данных-получателей к существующей группе доступности](http://blogs.msdn.com/b/sqlAlways%20On/archive/2012/02/01/use-log-shipping-to-prepare-secondary-databases-for-an-existing-availability-group.aspx)  
  
     [Блоги команды разработчиков SQL Server AlwaysOn: официальный блог по SQL Server AlwaysOn](http://blogs.msdn.com/b/sqlAlways%20On/)  
  
     [Блоги инженеров CSS SQL Server](http://blogs.msdn.com/b/psssql/)  
  
-   **Технические документы**  
  
     [Руководство по миграции. Переход на группы доступности AlwaysOn с предыдущих развертываний, сочетающих зеркальное отображение базы данных и доставку журналов](http://msdn.microsoft.com/library/jj635217)  
  
     [Технические документы Майкрософт Microsoft по SQL Server 2012](http://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультантов по SQL Server](http://sqlcat.com/)  
  
## См. также:  
 [Сведения о доставке журналов (SQL Server)](../../../database-engine/log-shipping/about-log-shipping-sql-server.md)   
 [Обзор групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [Отслеживание групп доступности (SQL Server)](../../../database-engine/availability-groups/windows/monitoring-of-availability-groups-sql-server.md)  
  
  
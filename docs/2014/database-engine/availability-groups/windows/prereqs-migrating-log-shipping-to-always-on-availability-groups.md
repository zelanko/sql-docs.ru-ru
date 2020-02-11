---
title: Предварительные требования для перехода с доставки журналов на группы доступности AlwaysOn (SQL Server) | Документация Майкрософт
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 865e8d720e9977f582ac5ae8a0e75d995fc82629
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62789559"
---
# <a name="prerequisites-for-migrating-from-log-shipping-to-alwayson-availability-groups-sql-server"></a>Необходимые условия для выполнения перехода от использования доставки журналов к использованию групп доступности AlwaysOn (SQL Server)
  В этом разделе описаны предварительные условия для преобразования базы данных-источника доставки журналов вместе с одной или несколькими базами данных-получателями в базу данных-источник и базы данных-получатели AlwaysOn.  
  
> [!NOTE]  
>  В качестве первичной базы данных для доставки журналов вы можете настроить любую базу данных-источник или базу данных-получатель (по возможности предназначенную для чтения).  
  
 **В этом разделе:**  
  
-   [Предварительные требования для группы доступности](#AGPrereqsRealAddress)  
  
-   [Предварительные требования для доставки журналов](#LogShipPrereqs)  
  
-   [Связанные задачи](#RelatedTasks)  
  
-   [Связанное содержимое](#RelatedContent)  
  
##  <a name="AGPrereqsRealAddress"></a>Предварительные требования для группы доступности  
 Чтобы разрешить выполнение заданий резервного копирования в первичной реплике группы доступности, используйте следующие параметры резервного копирования групп доступности AlwaysOn:  
  
|Свойство|Параметр|  
|--------------|-------------|  
|Автоматическое резервное копирование группы доступности|Только в первичной реплике|  
|Приоритет резервного копирования первичной реплики.|>0|  
  
 **Дополнительные сведения:**  
  
 [Просмотр свойств группы доступности (SQL Server)](view-availability-group-properties-sql-server.md)  
  
 [Настройка резервного копирования на реплики доступности &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="LogShipPrereqs"></a>Предварительные требования для доставки журналов  
  
-   База данных-источник доставки журналов должна находиться на экземпляре [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , на котором размещается первоначальная или текущая первичная реплика группы доступности.  
  
-   Для преобразования базы данных-получателя доставки журнала в базу данных-получатель AlwaysOn необходимо:  
  
    -   использовать то же имя, что и у базы данных-источника.  
  
    -   Размещение на экземпляре сервера, на котором размещается вторичная реплика для группы доступности.  
  
 После выполнения задания резервного копирования для базы данных-источника отключите задание резервного копирования и после выполнения задания по восстановлению для выбранной базы данных-получателя отключите задание восстановления.  
  
 После создания всех баз данных-получателей для группы доступности при необходимости проведения резервного копирования во вторичных репликах нужно изменить параметры автоматического резервного копирования для группы доступности.  
  
 **Дополнительные сведения:**  
  
 [Преобразование конфигурации доставки журналов в группу доступности](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (блог SQL Server)  
  
##  <a name="RelatedTasks"></a> Связанные задачи  
 **Доставка журналов**  
  
-   [Обновление доставки журналов до SQL Server 2014 &#40;Transact-SQL&#41;](../../log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [Удалить SQL Server &#40;доставки журналов&#41;](../../log-shipping/remove-log-shipping-sql-server.md)  
  
 **Группы доступности AlwaysOn**  
  
-   [Использование мастера групп доступности &#40;SQL Server Management Studio&#41;](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [Используйте диалоговое окно Создание группы доступности &#40;SQL Server Management Studio&#41;](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [Создание группы доступности &#40;&#41;Transact-SQL](create-an-availability-group-transact-sql.md)  
  
-   [Создание SQL Server PowerShell &#40;группы доступности&#41;](../../../powershell/sql-server-powershell.md)  
  
-   [Присоединение базы данных-получателя к группе доступности &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [Настройка резервного копирования на реплики доступности &#40;SQL Server&#41;](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="RelatedContent"></a> См. также  
  
-   **Тех**  
  
     [Преобразование конфигурации доставки журналов в группу доступности](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx)  
  
     [Добавление базы данных-источника доставки журналов и баз данных-получателей в существующую группу доступности](https://blogs.msdn.com/b/sqlalwayson/archive/2012/02/01/use-log-shipping-to-prepare-secondary-databases-for-an-existing-availability-group.aspx)  
  
     [Блоги группы разработчиков SQL Server AlwaysOn: официальный блог группы разработчиков SQL Server AlwaysOn](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [Блоги SQL Server инженеров CSS](https://blogs.msdn.com/b/psssql/)  
  
-   **Технические документы**  
  
     [Руководство по миграции. Переход на группы доступности AlwaysOn с предыдущих развертываний, сочетающих зеркальное отображение базы данных и доставку журналов](https://msdn.microsoft.com/library/jj635217)  
  
     [Технические документы Майкрософт для SQL Server 2012](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [Технические документы группы консультирования клиентов SQL Server](http://sqlcat.com/)  
  
## <a name="see-also"></a>См. также:  
 [SQL Server &#40;доставки журналов&#41;](../../log-shipping/about-log-shipping-sql-server.md)   
 [Общие сведения о группы доступности AlwaysOn &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [Мониторинг групп доступности &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md)  
  
  

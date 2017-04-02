---
title: "Установка ядра СУБД SQL | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ядро СУБД [SQL Server], установка"
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
caps.latest.revision: 45
author: "MikeRayMSFT"
ms.author: "mikeray"
manager: "jhubbard"
caps.handback.revision: 45
---
# Установка ядра СУБД SQL
  Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] входит в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и является основной службой, предназначенной для хранения, обработки и обеспечения безопасности данных. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] обеспечивает управляемый доступ к ресурсам и быструю обработку транзакций, что позволяет использовать его даже с самыми требовательными приложениями по обработке данных на предприятии.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает до 50 экземпляров компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на одном компьютере. Инструкции по созданию типовой установки [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] см. в статье [Установка SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/install-sql-server-2016-from-the-installation-wizard-setup.md).  
  
 **Внимание!** Для локальной установки программа установки должна запускаться от имени администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.  
  
 Если на странице «Компоненты для установки» мастера установки **[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] выбран компонент** Database Engine [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , то будут установлены следующие компоненты:  
  
-   [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
-   Репликация ― это необязательный компонент  
  
-   Full-Text Search ― это необязательный компонент  
  
-   Службы Data Quality Services являются необязательным компонентом.  
  
    > [!NOTE]  
    >  В этом выпуске установка флажка **Службы Data Quality Services** в программе установки не приводит к установке сервера служб Data Quality Services (DQS). Для установки сервера DQS необходимо выполнить дополнительные шаги после завершения установки. Дополнительные сведения см. в разделе [Install Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md).  
  
 Следующие дополнительные возможности могут применяться во многих типичных пользовательских сценариях.  
  
-   Клиент Data Quality  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]  
  
-   Компоненты соединения  
  
-   Модели программирования  
  
-   Средства управления  
  
-   [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]  
  
-   Компоненты документации  
  
> [!NOTE]  
>  По умолчанию при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы баз данных и образцы кода не устанавливаются. Дополнительные сведения об установке образцов баз данных и образцов кода см. на [веб-сайте CodePlex](http://go.microsoft.com/fwlink/?LinkId=87843).  
  
## См. также:  
 [Возможности, поддерживаемые различными выпусками SQL Server 2016](../Topic/Features%20Supported%20by%20the%20Editions%20of%20SQL%20Server%202016.md)   
 [Выпуски и компоненты SQL Server 2016](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Решения высокого уровня доступности (SQL Server)](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Обновление до SQL Server 2016 с помощью мастера установки (программа установки)](../../database-engine/install-windows/upgrade-to-sql-server-2016-using-the-installation-wizard-setup.md)  
  
  
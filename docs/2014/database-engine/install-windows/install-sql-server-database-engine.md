---
title: Сведения о SQL Server ядро СУБД | Документация Майкрософт
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], installing
ms.assetid: d0876e7f-aa52-4dd7-bd5c-029e2ffded5f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6373f67d40b9da97f652f3bcb05b3414deab5c8d
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62779365"
---
# <a name="about-the-sql-server-database-engine"></a>О компоненте SQL Server Database Engine
  Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] входит в состав [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и является основной службой, предназначенной для хранения, обработки и обеспечения безопасности данных. Компонент [!INCLUDE[ssDE](../../includes/ssde-md.md)] обеспечивает управляемый доступ к ресурсам и быструю обработку транзакций, что позволяет использовать его даже с самыми требовательными приложениями по обработке данных на предприятии.  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] поддерживает до 50 экземпляров компонента [!INCLUDE[ssDE](../../includes/ssde-md.md)] на одном компьютере. Сведения о создании типичной [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки см. в разделе [Install SQL Server 2014 мастера установки &#40;&#41;установки ](install-sql-server-from-the-installation-wizard-setup.md).  
  
 **Внимание!** Для локальной установки программа установки должна запускаться от имени администратора. При установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] из удаленной общей папки необходимо использовать учетную запись домена с разрешениями на чтение и выполнение для удаленной общей папки.  
  
 Следующие компоненты устанавливаются при выборе ** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ядро СУБД** на странице компоненты для установки мастера [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] установки.  
  
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
>  По умолчанию при установке [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] образцы баз данных и образцы кода не устанавливаются. Дополнительные сведения об установке образцов баз данных и образцов кода см. на [веб-сайте CodePlex](https://go.microsoft.com/fwlink/?LinkId=87843).  
  
## <a name="see-also"></a>См. также  
 [Функции, поддерживаемые различными выпусками SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)   
 [Выпуски и компоненты SQL Server 2014](../../sql-server/editions-and-components-of-sql-server-2016.md)   
 [Планирование установки SQL Server](../../sql-server/install/planning-a-sql-server-installation.md)   
 [Решения для обеспечения высокого уровня доступности &#40;SQL Server&#41;](../../sql-server/failover-clusters/high-availability-solutions-sql-server.md)   
 [Обновление до SQL Server 2014 с помощью мастера установки &#40;установки&#41;](upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  

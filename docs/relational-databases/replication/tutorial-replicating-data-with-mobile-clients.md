---
title: "Руководство. Репликация данных с мобильными клиентами | Документация Майкрософт"
ms.custom: 
ms.date: 03/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
helpviewer_keywords:
- replication [SQL Server], tutorials
ms.assetid: af673514-30c7-403a-9d18-d01e1a095115
caps.latest.revision: 
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8a11cf12fc057aba0f014fc36014fde9a52eda2a
ms.sourcegitcommit: ab25b08a312d35489a2c4a6a0d29a04bbd90f64d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/08/2018
---
# <a name="tutorial-replicating-data-with-mobile-clients"></a>Учебник. Репликация данных с мобильными клиентами
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
Репликация является хорошим решением проблемы перемещения данных между центральным сервером и мобильными клиентами, не имеющими постоянного подключения. С помощью мастеров репликации можно легко настроить и администрировать топологию репликации. В этом учебнике демонстрируется, как настроить топологию репликации для мобильных клиентов.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
В этом учебнике используется репликация слиянием, чтобы опубликовать данные из центральной базы данных для одного или более мобильных пользователей так, что каждый пользователь получит уникальным образом фильтрованное подмножество данных. На первом занятии рассматривается, как создать публикацию при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . На последующих занятиях рассматривается, как создать и синхронизировать подписку.  
  
## <a name="requirements"></a>Требования  
Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный опыт работы с репликацией. Перед тем как приступить к работе с этим учебником, необходимо освоить [Учебник. Подготовка сервера к репликации](../../relational-databases/replication/tutorial-preparing-the-server-for-replication.md).  
  
Для работы с этим учебником в системе должны быть установлены следующие компоненты:  
  
-   На сервере-издателе (источник):  
  
    -   Любой выпуск [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], за исключением Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) или [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Эти выпуски не могут быть издателями репликации.  
  
    -   Образец базы данных [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] . В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются.  
  
-   На сервере-подписчике (целевом):  
  
    -   Любой выпуск [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], за исключением [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)] не поддерживается публикацией, созданной в этом учебнике.  
  
    > [!NOTE]  
    > По умолчанию на [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]репликация не устанавливается.  
  
> [!NOTE]  
> В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]необходимо подключиться к издателю и подписчику с помощью имени входа, которое является членом предопределенной роли сервера sysadmin.  
  
**Предполагаемое время для выполнения заданий данного учебника: 30 минут.**  
  
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника  
  
-   [Урок 1. Публикация данных с помощью репликации слиянием](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
-   [Занятие 2. Создание подписки на публикацию слиянием](../../relational-databases/replication/lesson-2-creating-a-subscription-to-the-merge-publication.md)  
  
[Приступить к изучению](../../relational-databases/replication/lesson-1-publishing-data-using-merge-replication.md)  
  
## <a name="see-also"></a>См. также:  
[Основные понятия программирования репликации](../../relational-databases/replication/concepts/replication-programming-concepts.md)  
  
  
  

---
title: Руководство. Репликация данных между постоянно соединенными серверами | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- tutorials [SQL Server replication]
- replication [SQL Server], tutorials
- wizards [SQL Server replication]
ms.assetid: 7b18a04a-2c3d-4efe-a0bc-c3f92be72fd0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 32b97d456c42eab89511d8f5a9d1924914ea81ca
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62655400"
---
# <a name="tutorial-replicating-data-between-continuously-connected-servers"></a>Учебник. Репликация данных между постоянно соединенными серверами
  Репликация представляет собой хорошее решение проблемы перемещения данных между постоянно соединенными серверами. С помощью мастеров репликации можно легко настроить и администрировать топологию репликации. В этом учебники рассказывается о настройке топологии репликации для постоянно соединенных серверов.  
  
## <a name="what-you-will-learn"></a>Обзор учебника  
 В этом учебнике рассказывается о публикации данных из одной базы данных в другую при помощи репликации транзакций. На первом занятии рассматривается, как создать публикацию при помощи среды [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . На дальнейших занятиях разбирается создание и проверка подписки, а также измерение задержки.  
  
## <a name="requirements"></a>Требования  
 Этот учебник предназначен для пользователей, знакомых с основными операциями с базами данных, но имеющих ограниченный опыт в работе с репликацией. Для работы с этим учебником требуется завершить работу с предыдущим учебником, [Подготовка сервера для репликации](tutorial-preparing-the-server-for-replication.md).  
  
 Для работы с этим учебником должны быть установлены следующие компоненты.  
  
-   На сервере-издателе (источник):  
  
    -   Любой выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], за исключением Express ([!INCLUDE[ssExpress](../../includes/ssexpress-md.md)]) или [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Эти выпуски не могут быть издателями репликации.  
  
    -   [!INCLUDE[ssSampleDBUserInputNonLocal](../../includes/sssampledbuserinputnonlocal-md.md)]образец базы данных. В целях повышения безопасности образцы баз данных по умолчанию не устанавливаются.  
  
-   На сервере-подписчике (целевом):  
  
    -   Любой выпуск [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], за исключением [!INCLUDE[ssEW](../../includes/ssew-md.md)]. [!INCLUDE[ssEW](../../includes/ssew-md.md)]не может быть подписчиком в репликации транзакций.  
  
    > [!NOTE]  
    >  Репликация не устанавливается по умолчанию на [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] .  
  
> [!NOTE]  
>  В среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]необходимо подключиться к издателю и подписчику с помощью имени входа, которое является членом предопределенной роли сервера **sysadmin** .  
  
 **Предполагаемое время для выполнения заданий данного учебника: 30 минут.**  
  
## <a name="lessons-in-this-tutorial"></a>Занятия этого учебника  
  
-   [Занятие 1. Публикация данных с помощью репликации транзакций](lesson-1-publishing-data-using-transactional-replication.md)  
  
-   [Занятие 2. Создание подписки на публикацию транзакций](lesson-2-creating-a-subscription-to-the-transactional-publication.md)  
  
-   [Занятие 3. Проверка подписки и измерение задержки](lesson-3-validating-the-subscription-and-measuring-latency.md)  
  
 [Запуск учебника](transactional/transactional-replication.md)  
  
## <a name="see-also"></a>См. также:  
 [Основные понятия программирования репликации](concepts/replication-programming-concepts.md)  
  
  

---
title: Свойства публикации, страница "Общие" | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.general.f1
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 197a3648175fb65fdcd2861a7025237121c5eb6d
ms.sourcegitcommit: 022d67cfbc4fdadaa65b499aa7a6a8a942bc502d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37352846"
---
# <a name="publication-properties-general"></a>Свойства публикации, страница «Общие»
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Страница **Общие** диалогового окна **Свойства публикации** содержит основные сведения о публикации, включая ее имя, описание и порядок истечения срока ее действия.  
  
## <a name="options"></a>Параметры  
 **Название**  
 Имя публикации (только для чтения).  
  
 **База данных**  
 Имя базы данных публикации (только для чтения).  
  
 **Описание**  
 Описание публикации.  
  
 **Тип**  
 Тип публикации (только для чтения).  
  
 **Окончание действия подписки**  
 Выберите один из параметров срока действия публикации: **Бессрочные подписки** или **Подписки со сроком действия**с четко обозначенным периодом времени (**Интервал**).  
  
 Для публикаций моментальных снимков и публикаций транзакций [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует использовать в качестве значения по умолчанию **Бессрочные подписки**.  
  
 Для репликации слиянием [!INCLUDE[msCoName](../../includes/msconame-md.md)] рекомендует использовать в качестве значения по умолчанию **Подписки со сроком действия** и установить наиболее низкое значение из всех возможных для параметра **Интервал**. При увеличении срока действия подписки увеличивается и объем сохраняемых метаданных, что может негативно влиять на производительность системы. Найдите баланс между вероятностью возможных проблем с производительностью системы при обработке больших объемов метаданных и необходимостью для подписчиков не поддерживать соединение или хотя бы не осуществлять синхронизацию в течение продолжительного периода времени.  
  
 Дополнительные сведения см. в разделе [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Уровень совместимости**  
 Только для[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий и только для публикаций слиянием. Выберите минимально допустимую версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимую подписчикам для синхронизации с этой публикацией. Существует ряд правил, связанных с определением уровня совместимости.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  

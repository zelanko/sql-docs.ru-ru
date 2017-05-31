---
title: "Свойства публикации, страница &quot;Общие&quot; | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.general.f1
ms.assetid: 7912362f-c4d6-4f60-bd39-dee1f656ed18
caps.latest.revision: 25
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: bb22c4211fcf7d5e07f2105f221495cbadd8d9c6
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="publication-properties-general"></a>Свойства публикации, страница «Общие»
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
  
 Дополнительные сведения см. в статье [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Уровень совместимости**  
Только для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] и более поздних версий и только для публикаций слиянием. Выберите минимально допустимую версию [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , необходимую подписчикам для синхронизации с этой публикацией. Существует ряд правил, связанных с определением уровня совместимости.  
  
## <a name="see-also"></a>См. также:  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Просмотр и изменение свойств публикации](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Публикация данных и объектов базы данных](../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  

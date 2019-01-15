---
title: Проверка подписки | Документация Майкрософт
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.validateandresynch.f1
helpviewer_keywords:
- Validate Subscription dialog box
ms.assetid: 74bdf5e1-b886-4284-b5fb-332bf79ae083
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1983600c3eccc389bbc0a3a8995957688c173a37
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/09/2019
ms.locfileid: "54135144"
---
# <a name="validate-subscription"></a>Проверка подписки
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Используйте диалоговое окно **Проверка подписки** , чтобы установить, что подписка на публикацию слиянием должна быть проверена при следующем запуске агента слияния для этой подписки. Результаты подтверждения отображаются в мониторе репликации. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Кроме того, проверить все подписки на публикацию слиянием можно, щелкнув правой кнопкой мыши публикацию в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выбрав пункт **Проверить все подписки**.  
  
## <a name="options"></a>Параметры  
 **Дата последней попытки проверки**  
 Дата последнего сеанса работы агента слияния, в ходе которого производилась проверка подписки, независимо от успешности этой проверки.  
  
 **Дата последней успешной проверки**  
 Дата последнего сеанса работы агента слияния, в ходе которого была произведена успешная проверка подписки.  
  
 **Проверить эту подписку**  
 Выберите, чтобы проверить подписку.  
  
 **Параметры**  
 Нажмите, чтобы получить доступ к диалоговому окну **Параметры проверки подписки** , которое позволит указать, следует ли использовать проверку по количеству строк или по двоичной контрольной сумме.  
  
## <a name="see-also"></a>См. также:  
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  

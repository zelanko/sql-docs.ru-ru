---
title: "Настройка срока хранения распространения для публикаций транзакций | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
caps.latest.revision: "37"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: eb6f7ddde1dfb0546446bd4c0caee1075f182413
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Настройка срока хранения распространения для публикаций транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Укажите минимальный и максимальный сроки хранения в распространителе в диалоговом окне **Свойства базы данных распространителя — \<база_данных_распространителя>**. Его можно открыть на странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>**. Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Указание срока хранения на распространителе  
  
1.  На странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку свойств (**…**) для базы данных распространителя.  
  
2.  Для указания минимального срока хранения на распространителе введите значение в поле **Минимум** ; для указания максимального срока хранения на распространителе введите значение в поле **Но не более** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  

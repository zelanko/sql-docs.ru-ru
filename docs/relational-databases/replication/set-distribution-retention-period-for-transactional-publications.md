---
title: Настройка срока хранения распространения для публикаций транзакций | Документация Майкрософт
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e39be7010f24f33ae7f31217c7eba8c5b467654
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68051709"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Настройка срока хранения распространения для публикаций транзакций
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Укажите минимальный и максимальный срок хранения на распространителе в диалоговом окне **Свойства базы данных распространителя — \<база_данных_распространителя>** . Его можно открыть на странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** . Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Указание срока хранения на распространителе  
  
1.  На странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку свойств ( **...** ) для базы данных распространителя.  
  
2.  Для указания минимального срока хранения на распространителе введите значение в поле **Минимум** ; для указания максимального срока хранения на распространителе введите значение в поле **Но не более** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Окончание срока действия и отключение подписки](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  

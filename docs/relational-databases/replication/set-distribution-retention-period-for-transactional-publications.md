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
monikerRange: =azuresqldb-mi-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 9092662f88410812bd6c1c2035e8d04cfa9dd434
ms.sourcegitcommit: 2a06c87aa195bc6743ebdc14b91eb71ab6b91298
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/25/2019
ms.locfileid: "72907936"
---
# <a name="set-distribution-retention-period-for-transactional-publications"></a>Настройка срока хранения распространения для публикаций транзакций
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Укажите минимальный и максимальный срок хранения на распространителе в диалоговом окне **Свойства базы данных распространителя — \<база_данных_распространителя>** . Его можно открыть на странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** . Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Указание срока хранения на распространителе  
  
1.  На странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку свойств ( **...** ) для базы данных распространителя.  
  
2.  Для указания минимального срока хранения на распространителе введите значение в поле **Минимум** ; для указания максимального срока хранения на распространителе введите значение в поле **Но не более** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

## <a name="see-also"></a>См. также:  
 [Настройка распространения](../../relational-databases/replication/configure-distribution.md)   
 [Окончание срока действия и отключение подписки](../../relational-databases/replication/subscription-expiration-and-deactivation.md)  
  
  

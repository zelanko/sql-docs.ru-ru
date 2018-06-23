---
title: Настроить срок хранения на распространителе для публикаций транзакций (среда SQL Server Management Studio) | Документы Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transaction retention periods [SQL Server replication]
- retention periods [SQL Server replication]
ms.assetid: 9a98c53a-fea5-4235-b23d-6c69587c5676
caps.latest.revision: 35
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: ad1a697d6e139939723296fd481b2bbdb15cc39e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36101720"
---
# <a name="set-the-distribution-retention-period-for-transactional-publications-sql-server-management-studio"></a>настроить срок хранения на распространителе для публикаций транзакций (среда SQL Server Management Studio)
  Укажите минимальный и максимальный срок хранения на распространителе в диалоговом окне **Свойства базы данных распространителя — \<база_данных_распространителя>**. Его можно открыть на странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>**. Дополнительные сведения о доступе к этому диалоговому окну см. в статье [Просмотр и изменение свойств издателя и распространителя](view-and-modify-distributor-and-publisher-properties.md).  
  
### <a name="to-specify-the-distribution-retention-period"></a>Указание срока хранения на распространителе  
  
1.  На странице **Общие** диалогового окна **Свойства распространителя — \<распространитель>** нажмите кнопку свойств (**…**) для базы данных распространителя.  
  
2.  Для указания минимального срока хранения на распространителе введите значение в поле **Минимум** ; для указания максимального срока хранения на распространителе введите значение в поле **Но не более** .  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Настройка распространения](configure-distribution.md)   
 [Окончание срока действия и отключение подписки](subscription-expiration-and-deactivation.md)  
  
  
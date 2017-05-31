---
title: "Параметры проверки подписки (транзакционные подписки) | Документация Майкрософт"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
caps.latest.revision: 18
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: da21a38bf0797bf5368ddba1d1c2a47824bad369
ms.contentlocale: ru-ru
ms.lasthandoff: 04/11/2017

---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Параметры проверки подписки (подписки на публикацию транзакций)
  Используйте диалоговое окно **Параметры проверки подписки** для определения, должна ли проверка правильности использовать только количество строк или количество строк и двоичную контрольную сумму.  
  
## <a name="options"></a>Параметры  
 **Проверить, совпадают ли числа реплицированных строк данных у подписчика и у издателя**  
 Выберите для выполнения тип проверки количества строк. Для публикаций Oracle единственный доступный параметр — это параметр **Выполнить подсчет действительного числа строк путем непосредственных запросов к таблицам**.  
  
 **Сравнить контрольные суммы для проверки правильности данных в строке**  
 Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью двоичного алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется.  
  
 **Остановить агент распространителя после завершения проверки**  
 По умолчанию агент распространителя работает постоянно. Выберите этот параметр для остановки агента после выполнения проверки. Это позволяет удостовериться в успешном завершении проверки перед продолжением копирования данных к подписчику.  
  
## <a name="see-also"></a>См. также:  
 [Проверка данных на подписчике](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-replicated-data.md)  
  
  

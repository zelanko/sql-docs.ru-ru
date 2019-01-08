---
title: Параметры проверки подписки (подписки слиянием) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.mergeoptions.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: 4958c4ab-2025-42ce-b836-6fb4e9e6f24d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a10b4878aca674d3710d30d2cb70c5a377caebc6
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/03/2018
ms.locfileid: "52790636"
---
# <a name="subscription-validation-options-merge-subscriptions"></a>Параметры проверки подписки (подписка на публикацию слиянием)
  Используйте диалоговое окно **Параметры проверки подписки** для указания, нужно ли при проверке использовать только количество строк или количество строк и двоичную контрольную сумму.  
  
## <a name="options"></a>Параметры  
 **Проверить только количество строк**  
 Выберите этот параметр, чтобы убедиться, что таблица на подписчике имеет то же количество строк, что и таблица на издателе. Этот метод не проверяет соответствие содержимого строк. Проверка количества строк обеспечивает упрощенный подход к проверке, который может уведомить о проблемах с данными.  
  
 **Проверить количество строк и сравнить контрольные суммы для проверки правильности данных в строке**  
 Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью двоичного алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется. Этот параметр недопустим для [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проверка данных на подписчике](validate-data-at-the-subscriber.md)   
 [Проверка реплицированных данных](validate-replicated-data.md)  
  
  

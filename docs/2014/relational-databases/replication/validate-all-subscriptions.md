---
title: Инициализация всех подписок | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
caps.latest.revision: 23
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6df15aecb19b61bc5cdb22e587177c0cca71da5
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2018
ms.locfileid: "37203012"
---
# <a name="validate-all-subscriptions"></a>Проверка всех подписок
  Чтобы указать, что все подписки на публикацию слиянием должны быть проверены при следующем запуске агента слияния, для каждой подписки используется диалоговое окно **Проверка всех подписок** . Результаты подтверждения отображаются в мониторе репликации. Дополнительные сведения см. в статье [Validate Data at the Subscriber](validate-data-at-the-subscriber.md).  
  
 Отдельную подписку можно проверить, щелкнув ее правой кнопкой мыши в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выбрав пункт **Проверка подписки**.  
  
## <a name="options"></a>Параметры  
 **Проверить только количество строк**  
 Выберите этот параметр, чтобы убедиться, что таблица на подписчике имеет то же количество строк, что и таблица на издателе. Этот метод не проверяет соответствие содержимого строк. Проверка количества строк обеспечивает упрощенный подход к проверке, который может уведомить о проблемах с данными.  
  
 **Проверить количество строк и сравнить контрольные суммы для проверки правильности данных в строке**  
 Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью двоичного алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется. Этот параметр недопустим для [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проверка реплицированных данных](validate-replicated-data.md)  
  
  

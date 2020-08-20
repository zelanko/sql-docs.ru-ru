---
description: Проверка всех подписок
title: Инициализация всех подписок | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.allsubscriptions.f1
helpviewer_keywords:
- Validate All Subscriptions dialog box
ms.assetid: 32e31469-36e4-42d9-a57a-12388bfd229d
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: f2302499c6ea6a17e165f647823b3dfb6a48895f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88455560"
---
# <a name="validate-all-subscriptions"></a>Проверка всех подписок
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Чтобы указать, что все подписки на публикацию слиянием должны быть проверены при следующем запуске агента слияния, для каждой подписки используется диалоговое окно **Проверка всех подписок** . Результаты подтверждения отображаются в мониторе репликации. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Отдельную подписку можно проверить, щелкнув ее правой кнопкой мыши в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выбрав пункт **Проверка подписки**.  
  
## <a name="options"></a>Параметры  
 **Проверить только количество строк**  
 Выберите этот параметр, чтобы убедиться, что таблица на подписчике имеет то же количество строк, что и таблица на издателе. Этот метод не проверяет соответствие содержимого строк. Проверка количества строк обеспечивает упрощенный подход к проверке, который может уведомить о проблемах с данными.  
  
 **Проверить количество строк и сравнить контрольные суммы для проверки правильности данных в строке**  
 Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью двоичного алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется. Этот параметр недопустим для [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  

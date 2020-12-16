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
monikerRange: =azuresqldb-current||>=sql-server-2016
ms.openlocfilehash: a050ee7d8f018277f4bb55726cd1e674c0ee7e68
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97475635"
---
# <a name="validate-all-subscriptions"></a>Проверка всех подписок
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Чтобы указать, что все подписки на публикацию слиянием должны быть проверены при следующем запуске агента слияния, для каждой подписки используется диалоговое окно **Проверка всех подписок** . Результаты подтверждения отображаются в мониторе репликации. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Отдельную подписку можно проверить, щелкнув ее правой кнопкой мыши в среде [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выбрав пункт **Проверка подписки**.  
  
## <a name="options"></a>Варианты  
 **Проверить только количество строк**  
 Выберите этот параметр, чтобы убедиться, что таблица на подписчике имеет то же количество строк, что и таблица на издателе. Этот метод не проверяет соответствие содержимого строк. Проверка количества строк обеспечивает упрощенный подход к проверке, который может уведомить о проблемах с данными.  
  
 **Проверить количество строк и сравнить контрольные суммы для проверки правильности данных в строке**  
 Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью двоичного алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется. Этот параметр недопустим для [!INCLUDE[ssEW](../../includes/ssew-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  

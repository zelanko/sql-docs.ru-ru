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
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: e95a160e405adb8cdc77a763840489b436c9bf96
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87110531"
---
# <a name="validate-subscription"></a>Проверка подписки
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Используйте диалоговое окно **Проверка подписки** , чтобы установить, что подписка на публикацию слиянием должна быть проверена при следующем запуске агента слияния для этой подписки. Результаты подтверждения отображаются в мониторе репликации. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
 Кроме того, проверить все подписки на публикацию слиянием можно, щелкнув правой кнопкой мыши публикацию в среде [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] и выбрав пункт **Проверить все подписки**.  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
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
  
  

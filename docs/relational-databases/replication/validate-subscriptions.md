---
title: Проверка подписок | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.subscriptions.f1
helpviewer_keywords:
- Validate Subscriptions dialog box
ms.assetid: 0ca39a35-f22c-46c5-82a4-342e34bf5d1b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 79079774fe3b13e61a9bbdb32c767c2f40576b66
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87110520"
---
# <a name="validate-subscriptions"></a>Проверка подписок
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Диалоговое окно **Проверить подписки** позволяет указать подписки на публикации транзакций, которые нужно проверить в следующий раз агентом распространителя при каждом запуске подписки. Результаты подтверждения отображаются в мониторе репликации. Дополнительные сведения см. в разделе [Validate Data at the Subscriber](../../relational-databases/replication/validate-data-at-the-subscriber.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Параметры  
 **Проверить все подписки SQL Server**  
 Выберите, чтобы проверить все подписки SQL Server на данную публикацию.  
  
 **Проверить следующие подписки**  
 Выберите, если не нужно проверять все подписки. Выберите из списка подписки, которые нужно проверять.  
  
 **Параметры проверки**  
 Нажмите, чтобы получить доступ к диалоговому окну **Параметры проверки подписки** , которое позволит указать, следует ли использовать проверку по количеству строк или по двоичной контрольной сумме.  
  
## <a name="see-also"></a>См. также:  
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  

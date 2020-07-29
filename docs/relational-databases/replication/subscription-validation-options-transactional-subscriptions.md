---
title: Диалоговое окно "Параметры проверки подписки" (транзакционные)
description: Здесь описывается диалоговое окно "Параметры проверки подписки" для репликации транзакций в SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.validate.options.f1
helpviewer_keywords:
- Subscription Validation Options dialog box
ms.assetid: fd66ad1f-df01-4240-9e89-8f41bff12c1e
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: a3bf4ef316337050ae6e9c48659b1b1250ea6a08
ms.sourcegitcommit: 768f046107642f72693514f51bf2cbd00f58f58a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/23/2020
ms.locfileid: "87111728"
---
# <a name="subscription-validation-options-transactional-subscriptions"></a>Параметры проверки подписки (подписки на публикацию транзакций)
[!INCLUDE[sql-asdb](../../includes/applies-to-version/sql-asdb.md)]
  Используйте диалоговое окно **Параметры проверки подписки** для определения, должна ли проверка правильности использовать только количество строк или количество строк и двоичную контрольную сумму. 

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Параметры  
 **Проверить, совпадают ли числа реплицированных строк данных у подписчика и у издателя**  
 Выберите для выполнения тип проверки количества строк. Для публикаций Oracle единственный доступный параметр — это параметр **Выполнить подсчет действительного числа строк путем непосредственных запросов к таблицам**.  
  
 **Сравнить контрольные суммы для проверки правильности данных в строке**  
 Кроме подсчета количества строк на подписчике и на издателе, вычисляется контрольная сумма всех данных с помощью двоичного алгоритма подсчета контрольной суммы. Если количество строк не совпадает, то контрольная сумма не проверяется.  
  
 **Остановить агент распространителя после завершения проверки**  
 По умолчанию агент распространителя работает постоянно. Выберите этот параметр для остановки агента после выполнения проверки. Это позволяет удостовериться в успешном завершении проверки перед продолжением копирования данных к подписчику.  
  
## <a name="see-also"></a>См. также:  
 [Проверка данных на подписчике](../../relational-databases/replication/validate-data-at-the-subscriber.md)   
 [Проверка реплицированных данных](../../relational-databases/replication/validate-data-at-the-subscriber.md)  
  
  

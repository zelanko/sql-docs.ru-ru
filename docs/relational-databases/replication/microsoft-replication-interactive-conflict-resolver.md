---
description: Интерактивный сопоставитель конфликтов репликации (Microsoft)
title: Интерактивный сопоставитель конфликтов (слияние)
describes: Describes the Interactive Conflict Resolver that can be used for merge subscriptions that are synchronized using the Windows Synchronization Manager.
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.replconflictviewer.interactiveresolver.f1
ms.assetid: d3d4a480-782b-4b1d-b839-565c8cf6cb24
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2016
ms.openlocfilehash: a0cbd836bc0a7676128067f44e4079d4901de962
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2020
ms.locfileid: "97464725"
---
# <a name="microsoft-replication-interactive-conflict-resolver"></a>Интерактивный сопоставитель конфликтов репликации (Microsoft)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]
  Интерактивный сопоставитель конфликтов может применяться для подписок на публикации слиянием, которые синхронизируются с помощью диспетчера синхронизации Windows. Он позволяет просматривать, сравнивать, редактировать и выбирать результаты для конфликтов данных. Репликация также содержит средство просмотра конфликтов, позволяющее просматривать и изменять результаты конфликта после их фиксации. Интерактивный сопоставитель конфликтов позволяет выбирать результаты во время выполнения синхронизации.  
  
> [!NOTE]  
>  Конфликты, затрагивающие логические записи, не отображаются в интерактивном сопоставителе. Для просмотра сведений о таких конфликтах используются хранимые процедуры репликации. Дополнительные сведения см. в статье [Просмотр сведений о конфликтах для публикаций слиянием &#40;программирование репликации на языке Transact-SQL&#41;](./view-and-resolve-data-conflicts-for-merge-publications.md).  
  
## <a name="options"></a>Параметры  
 **Имя столбца**  
 Имена всех столбцов в таблице. Один или несколько столбцов могли содержать конфликтующие данные. Независимо от того, какие столбцы конфликтуют, вся строка, в пользу которой был разрешен конфликт, переписывает всю проигравшую строку.  
  
 **Предлагаемое разрешение**  
 Сопоставитель конфликтов предлагает разрешение для статьи.  
  
 **Издатель**  
 Значение данных на издателе.  
  
 **Подписчик**  
 Значение данных на подписчике.  
  
 **Принять предлагаемый вариант**, **Принять вариант издателя** и **Принять вариант подписчика**  
 Щелкните, чтобы принять строку, которая будет применена на издателе или подписчике, в зависимости от того, в пользу какого участника был разрешен конфликт. Если конфликт был разрешен в пользу подписчика, все другие подписчики получат победившую в конфликте строку при следующей их синхронизации с издателем.  
  
 **Разрешить оставшиеся конфликты автоматически**  
 Автоматическое разрешение оставшихся конфликтов с помощью предлагаемого разрешения, предоставляемого для статьи сопоставителем конфликтов.  
  
 **Регистрация подробностей конфликта для последующего обращения**  
 Регистрация подробностей конфликта в системные таблицы.  
  
## <a name="see-also"></a>См. также  
 [Интерактивное разрешение конфликтов](../../relational-databases/replication/merge/advanced-merge-replication-conflict-interactive-resolution.md)   
 [Просмотр и разрешение конфликтов данных для публикации слиянием (SQL Server Management Studio)](../../relational-databases/replication/view-and-resolve-data-conflicts-for-merge-publications.md)   
 [Синхронизация подписки с помощью диспетчера синхронизации Windows (Windows Synchronization Manager)](../../relational-databases/replication/synchronize-a-subscription-using-windows-synchronization-manager.md)   
 [Advanced Merge Replication Conflict Detection and Resolution](../../relational-databases/replication/merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  

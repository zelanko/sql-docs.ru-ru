---
title: Обновление ядра СУБД | Документы Майкрософт
description: В этой статье приводятся ссылки на ресурсы, которые помогут вам обновить ядро СУБД SQL Server предыдущего выпуска SQL Server до SQL Server 2019.
ms.custom: ''
ms.date: 11/04/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433859
author: cawrites
ms.author: chadam
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: e527cbe28eb2685d79d37393396508a0c316677d
ms.sourcegitcommit: 5a1ed81749800c33059dac91b0e18bd8bb3081b1
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/23/2020
ms.locfileid: "96125773"
---
# <a name="upgrade-database-engine"></a>Обновление [компонент ядра СУБД]

 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
  Статьи в этом разделе помогут вам обновить ядро СУБД [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] предыдущего выпуска [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
1.  [Выбор метода обновления ядра СУБД](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md). Прежде всего вам необходимо понять различные методы обновления. В этой статье рассматриваются различные методы обновления и действия, связанные с каждым из них.  
  
2.  [Составление и тестирование плана обновления ядра СУБД](../../database-engine/install-windows/plan-and-test-the-database-engine-upgrade-plan.md). Ознакомившись с методами обновления, вы будете готовы разработать соответствующий метод обновления для используемой среды разработки, а затем проверить его перед обновлением существующей среды. В этой статье рассматривается разработка плана обновления и его тестирование.  
  
3.  [Завершение обновления ядра СУБД](../../database-engine/install-windows/complete-the-database-engine-upgrade.md). После обновления ядра СУБД до [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] и перевода баз данных в режим "в сети" необходимо выполнить дополнительные действия, включая создание резервной копии, обновление баз данных для включения новых функций и повторное заполнение полнотекстовых каталогов. Эти действия рассматриваются в данной статье.  
  
4.  Обновите [уровень совместимости базы данных](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#compatibility-levels-and-database-engine-upgrades) (**применимо к**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] и [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]). Одним из действий, выполняемых после перевода баз данных в режим "в сети" в новой версии [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] или [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)], может быть обновление функционального режима баз данных для включения новых функций путем изменения уровня совместимости базы данных. Это можно сделать вручную или посредством Помощника по настройке запросов. 

    - [Изменение режима совместимости базы данных и использование хранилища запросов](../../database-engine/install-windows/change-the-database-compatibility-mode-and-use-the-query-store.md). После изменения уровня совместимости базы данных вручную используйте хранилище запросов, чтобы отслеживать производительность и обнаруживать ее снижение. В этой статье рассматривается этот процесс и приводятся рекомендации.  

    - [Изменение режима совместимости базы данных с помощью Помощника по настройке запросов](../../relational-databases/performance/upgrade-dbcompat-using-qta.md). Помимо изменения уровня совместимости базы данных вручную, можно использовать рекомендованный процесс, предоставляемый **Помощником по настройке запросов (QTA)** . В этой статье рассматривается этот процесс и приводятся рекомендации по работе с Помощником по настройке запросов.  

    Дополнительные сведения о новых возможностях и улучшениях, доступных после изменения уровня совместимости базы данных, см. в статье [Различия между уровнями совместимости](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md#compatibility-levels-and-stored-procedures).

5.  [Использование преимуществ новых функций SQL Server](https://www.microsoft.com/sql-server/sql-server-2019). Наконец, завершив предыдущие действия, вы будете готовы к изучению преимуществ новых усовершенствований ядра СУБД. В этой статье предлагаются некоторые из этих усовершенствований, а также ссылки на дополнительные сведения.  
  
  

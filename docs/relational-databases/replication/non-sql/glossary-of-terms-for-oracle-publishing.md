---
title: "Глоссарий терминов по публикации Oracle | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Oracle publishing [SQL Server replication], glossary
ms.assetid: e21dfa4b-6144-4be7-9cbf-ca2709b2bd9f
caps.latest.revision: "32"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 3cd8bced4b90589b56f5aa64c67efd842af68aba
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/17/2017
---
# <a name="glossary-of-terms-for-oracle-publishing"></a>Глоссарий терминов публикации Oracle
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Для администрирования и настройки конфигурации публикации Oracle нужно ознакомиться с указанной ниже терминологией Oracle. Полный список терминов Oracle см. в электронной документации Oracle.  
  
 Индексно организованные таблицы (IOT)  
 Таблица, данные которой физически отсортированы на диске в индексном порядке; аналог таблицы [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с кластеризованным индексом. IOT реплицируется на подписчик в виде таблицы с кластеризованным индексом.  
  
 Экземпляр  
 База данных Oracle связана с экземпляром. Экземпляр содержит память и фоновые процессы, поддерживающие базу данных. Экземпляр Oracle всегда сопоставляется с одной базой данных, тогда как экземпляр [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] может содержать множество баз данных. Существуют обстоятельства, при которых база данных Oracle может иметь несколько экземпляров.  
  
 Прослушиватель Oracle  
 Обрабатывает входящий сетевой трафик для экземпляра базы данных Oracle. При настройке сетевого подключения к базе данных Oracle указывается протокол, по которому отсылается трафик, и порт, на котором прослушиватель прослушивает трафик. Прослушиватель обычно настраивается на запуск на том же компьютере, на котором выполняется экземпляр базы данных Oracle, и может быть настроен для работы с одним или несколькими экземплярами.  
  
 ROWID  
 Указатель расположения определенной строки базы данных. Поскольку извлечение строк с использованием ROWID происходит быстрее, чем при использовании просмотра таблицы или индекса, репликация использует ROWID в течение периода обработки опубликованных изменений таблицы.  
  
 Последовательность  
 Объект базы данных, который используется для формирования уникальных чисел. Репликация использует последовательности дл упорядочивания изменений, произведенных в опубликованных таблицах.  
  
 SQL\*Plus  
 Приложение, используемое для доступа и отправки запросов к базам данных Oracle. Похоже на программу [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] **sqlcmd**.  
  
 Синоним  
 Псевдоним для объекта. При настройке издателя Oracle автоматически создается специальный открытый синоним **MSSQLSERVERDISTRIBUTOR** . Синоним ссылается на таблицу **HREPL_Distributor** и обеспечивает логический указатель на распространитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , обслуживающий издателя.  
  
 После публикации базы данных Oracle последующие попытки переустановить конфигурацию издателя для использования иного распространителя [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] будут неудачны, поскольку этот открытый синоним идентифицирует определенный распространитель с установленной конфигурацией для обслуживания издателя.  
  
 Табличное пространство  
 Элемент хранилища базы данных, примерно эквивалентный группе файлов в [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 Имя службы TNS  
 Протокол TNS (Transparent Network Substrate) — уровень связи, используемый базами данных Oracle. Имя службы TNS — это имя, с которым экземпляр базы данных Oracle представлен в сети. Имя службы TNS назначается при настройке подключений к базе данных Oracle. Репликация использует имя службы TNS для идентификации издателя и установки подключений.  
  
 Пользовательская схема  
 Пользовательская схема может рассматриваться как пользователь базы данных, владеющий определенным набором ее объектов. Схема администратора репликации владеет всеми объектами, созданными процессом репликации [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] в базе данных Oracle, за исключением открытого синонима **MSSQLSERVERDISTRIBUTOR** .  
  
## <a name="see-also"></a>См. также:  
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Объекты, создаваемые в издателе Oracle](../../../relational-databases/replication/non-sql/objects-created-on-the-oracle-publisher.md)   
 [Издатели, отличные от издателей SQL Server](../../../relational-databases/replication/non-sql/non-sql-server-publishers.md)   
 [Oracle Publishing Overview](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  

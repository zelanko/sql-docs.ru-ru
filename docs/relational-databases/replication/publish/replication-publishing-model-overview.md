---
title: Обзор модели публикации репликации | Документация Майкрософт
ms.custom: ''
ms.date: 09/01/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- replication [SQL Server], publishing model
- subscriptions [SQL Server replication], about subscriptions
- articles [SQL Server replication]
- publications [SQL Server replication]
- Publishers [SQL Server replication], about Publishers
- Subscribers [SQL Server replication]
- Distributors [SQL Server replication], about Distributors
- Subscribers [SQL Server replication], about Subscribers
- articles [SQL Server replication], about articles
- publications [SQL Server replication], about publications
- Distributors [SQL Server replication]
ms.assetid: b9567832-e6a8-45b2-a3ed-ea12aa002f4b
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: d0983db7dee94269981933f115594bdbb9c6a115
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287572"
---
# <a name="replication-publishing-model-overview"></a>Обзор модели публикации репликации
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Репликация использует метафору издательского дела, в основе топологии репликации лежат такие компоненты как издатель, распространитель, подписчики, публикации, статьи и подписки. Удобно представить репликацию [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с помощью терминологии журнала:  
  
-   Издатель журнала производит одну или несколько публикаций  
  
-   Публикация содержит статьи  
  
-   Издатель или распространяет журнал напрямую, или использует распространитель  
  
-   Подписчики получают публикации, на которые они подписались  
  
 Хотя сравнение с журналом полезно для понимания репликации, следует отметить, что репликация [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] включает возможности, которые не представлены в данной метафоре, в частности возможность подписчика выполнять обновления и возможность издателя посылать добавочные изменения в статьи публикации.  
  
 *Топология репликации* определяет отношения между серверами и копиями данных, и проясняет логику, определяющую порядок обмена данными между серверами. Существует несколько процессов репликации (называемых *агентами*), которые отвечают за копирование и перемещение данных между издателем и подписчиками. Следующая иллюстрация представляет собой обзор компонентов и процессов, входящих в репликацию.  
  
 ![Компоненты репликации и потоки данных](../../../relational-databases/replication/publish/media/replintro1.gif "Компоненты репликации и потоки данных")  
  
## <a name="publisher"></a>Издатель  
 Издатель — это экземпляр базы данных, который делает данные доступными в других местах посредством репликации. Издатель может иметь одну или более публикаций, каждая из которых определяет логически связный набор объектов и данных для репликации.  
  
## <a name="distributor"></a>Распространитель  
 Распространитель — это экземпляр базы данных, который действует как хранилище специальных данных репликации, связанных с одним или несколькими издателями. Каждый издатель связан с одной базой данных (называемой базой данных распространителя), располагающейся на распространителе. База данных распространителя хранит информацию о состоянии репликации, метаданные публикации, и иногда действует как очередь для перемещения данных с издателя на подписчики. Нередко единичный экземпляр сервера базы данных действует одновременно как издатель и как распространитель. Такой сервер базы известен как *локальный распространитель*. Когда издатель и распространитель настроены на разных экземплярах серверов баз данных, распространитель называют *удаленным распространителем*.  
  
## <a name="subscribers"></a>Подписчики  
 Подписчик — это экземпляр базы данных, который получает реплицированные данные. Подписчик может получать данные от нескольких издателей и публикаций. В зависимости от выбранного типа репликации подписчик может также передавать изменения данных издателю или переиздавать эти данные на другие подписчики.  
  
## <a name="article"></a>Статья  
 Статья определяет объект базы данных, включенный в публикацию. Публикация может содержать разные типы статей, включая таблицы, представления, хранимые процедуры и другие объекты. Если таблицы публикуются в виде статей, можно использовать фильтры для ограничения столбцов и строк данных, посылаемых подписчикам.  
  
## <a name="publication"></a>Публикация  
 Публикация — это коллекция из одной или нескольких статей, принадлежащих одной базе данных. Группирование нескольких статей в публикацию упрощает указание логически связанного набора объектов и данных базы данных, реплицируемых в виде единого блока.  
  
## <a name="subscription"></a>Подписка  
 Подписка — это запрос на доставку копии публикации подписчику. Подписка определяет, какая публикация будет получена, где и когда. Существует два типа подписок: по запросу и принудительные. Дополнительные сведения о подписках см. в статье [Подписка на публикации](../../../relational-databases/replication/subscribe-to-publications.md).  
  
## <a name="see-also"></a>См. также:  
 [Обзор агентов репликации](../../../relational-databases/replication/agents/replication-agents-overview.md)   
 [Types of Replication](../../../relational-databases/replication/types-of-replication.md)   
 [Настройка репликации для групп доступности AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/configure-replication-for-always-on-availability-groups-sql-server.md)   
 [Обслуживание базы данных публикации AlwaysOn (SQL Server)](../../../database-engine/availability-groups/windows/maintaining-an-always-on-publication-database-sql-server.md)  
  
  

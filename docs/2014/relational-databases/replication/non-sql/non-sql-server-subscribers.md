---
title: Подписчики, отличные от подписчиков SQL Server | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], non-SQL Server Subscribers
- heterogeneous data sources, non-SQL Server Subscribers
- heterogeneous data sources
- heterogeneous database replication, non-SQL Server Subscribers
- non-SQL Server Subscribers, about non-SQL Server Subscribers
- heterogeneous Subscribers
- heterogeneous Subscribers, about heterogeneous Subscribers
- Subscribers [SQL Server replication], non-SQL Server Subscribers
- non-SQL Server Subscribers
ms.assetid: 831e7586-2949-4b9b-a2f3-7b0b699b23ff
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 19516e1b90a04c29efdfc8175d003a30ddf7957c
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/02/2018
ms.locfileid: "48071064"
---
# <a name="non-sql-server-subscribers"></a>Подписчики, отличные от подписчиков SQL Server
  Следующие подписчики, не относящиеся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , могут подписаться на публикации моментальных снимков и публикации транзакций, используя принудительные подписки. Подписки поддерживаются для двух самых последних версий каждой из баз данных, приведенных в списке, с использованием самой последней версии поставщика OLE DB из приводимого списка.  
  
 Разнородная репликация на подписчики, отличные от подписчика SQL Server, устарела. Публикация Oracle устарела. Для перемещения данных создайте решения с помощью системы отслеживания измененных данных и служб [!INCLUDE[ssIS](../../../includes/ssis-md.md)].  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
|База данных|Операционная система|Поставщик|  
|--------------|----------------------|--------------|  
|Oracle;|Все платформы, поддерживаемые Oracle|Поставщик OLE DB для Oracle (поставляемый Oracle)|  
|IBM DB2|MVS, AS400, Unix, Linux, Windows, за исключением версии 9.x|Поставщик OLE DB для Microsoft Host Integration Server (HIS)|  
  
 Сведения о создании подписок для Oracle и IBM DB2 см. в разделах [Oracle Subscribers](oracle-subscribers.md) и [IBM DB2 Subscribers](ibm-db2-subscribers.md).  
  
## <a name="considerations-for-non-sql-server-subscribers"></a>Вопросы использования подписчиков, отличных от подписчиков SQL Server  
 При репликации на подписчики, не относящиеся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , необходимо помнить о следующем:  
  
### <a name="general-considerations"></a>Общие рекомендации  
  
-   Репликация поддерживает публикацию таблиц и индексированных представлений в виде таблиц для подписчиков, не относящихся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (индексированные представления не могут быть реплицированы как индексированные представления).  
  
-   Когда публикация создается в мастере создания публикаций, а затем включается для подписчиков, отличных от подписчиков SQL Server, с помощью диалогового окна «Свойства публикации», владелец всех объектов в базе данных подписки не указывается для подписчиков, отличных от подписчиков[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , в то время как для подписчиков [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] он устанавливается как владелец соответствующего объекта в базе данных публикации.  
  
-   Если публикация имеет подписчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] и подписчиков, не относящихся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , то публикация должна быть включена для подписчиков, не относящихся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , перед тем как будут созданы какие-либо подписки для подписчиков [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   По умолчанию скрипты, создаваемые агентом моментальных снимков для подписчиков, не относящихся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , используют в синтаксисе инструкции CREATE TABLE идентификаторы без кавычек. Поэтому опубликованная таблица с именем 'test' реплицируется как 'TEST'. Чтобы сохранить регистр символов для имени таблицы публикации, укажите для агента распространителя параметр **-QuotedIdentifier** . Параметр **-QuotedIdentifier** должен также применяться, если имена опубликованных объектов (таких как таблицы, столбцы и ограничения) содержат пробелы или слова, которые являются зарезервированными словами в той версии базы данных, которая используется на подписчике, не являющемся подписчиком[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения об этом параметре см. в разделе [Replication Distribution Agent](../agents/replication-distribution-agent.md).  
  
-   Учетная запись, под которой запускается агент распространителя, должна иметь доступ с правом на чтение к установочному каталогу поставщика OLE DB.  
  
-   По умолчанию для подписчиков, не являющихся подписчиками[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , агент распространителя использует значение [(адреса по умолчанию)] для базы данных подписки (параметр **-SubscriberDB** для агента распространителя):  
  
    -   Для СУБД Oracle сервер имеет не более одной базы данных, поэтому нет необходимости указывать базу данных.  
  
    -   Для СУБД IBM DB2 база данных указывается в строке соединения с DB2. Дополнительные сведения см. в статье [Создание подписки для подписчика, отличного от подписчика SQL Server](../create-a-subscription-for-a-non-sql-server-subscriber.md).  
  
-   Если распространитель [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] выполняется на 64-разрядной платформе, необходимо использовать 64-разрядную версию соответствующего поставщика OLE DB.  
  
-   Репликация перемещает данные в формате Юникода независимо от параметров сортировки и кодовых страниц, используемых на издателе и подписчике. При репликации между издателями и подписчиками рекомендуется выбрать совместимые параметры сортировки и кодовую страницу.  
  
-   Если статья добавляется или удаляется из публикации, то подписки для подписчиков, не относящихся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , должны быть повторно инициализированы.  
  
-   Для всех подписчиков, не относящихся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , поддерживаются только ограничения NULL и NOT NULL. Ограничения первичного ключа реплицируются как уникальные индексы.  
  
-   В разных базах данных значение NULL обрабатывается по-разному, что влияет на представление пустых значений, пустых строк и значений NULL. Это в свою очередь влияет на поведение значений, вставляемых в столбцы с определяемыми уникальными ограничениями. Например, СУБД Oracle допускает существование нескольких значений NULL в столбце, который считается уникальным, тогда как [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] допускает наличие только одного значения NULL в уникальном столбце.  
  
     Дополнительным фактором, который следует учитывать, является порядок обработки значений NULL, пустых строк и пустых значений в случае, когда столбец определяется как NOT NULL. Сведения по этому вопросу для подписчиков Oracle см. в разделе [Oracle Subscribers](oracle-subscribers.md).  
  
-   Связанные с репликацией метаданные (таблица последовательности транзакций) на поставщиках[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] не удаляются при удалении подписки.  
  
### <a name="conforming-to-the-requirements-of-the-subscriber-database"></a>Соответствие требованиям базы данных подписчика  
  
-   Опубликованные схема и данные должны соответствовать требованиям базы данных подписчика. Например, если база данных, не относящаяся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , имеет меньший максимальный размер строки, чем [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], то следует убедиться, что опубликованные схема и данные не превышают этот размер.  
  
-   Таблицы, которые реплицируются на подписчики, не относящиеся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , должны следовать соглашениям об именовании таблиц базы данных подписчика.  
  
-   DDL не поддерживается для подписчиков, отличных от подписчиков SQL Server. Дополнительные сведения об изменениях в схеме см. в разделе [Внесение изменений в схемы баз данных публикации](../publish/make-schema-changes-on-publication-databases.md).  
  
### <a name="replication-feature-support"></a>Поддержка возможности репликации  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предусматривает два типа подписок: по запросу и принудительную. Подписчики, не относящиеся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , должны использовать принудительные подписки, для которых агент распространителя запускается на распространителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] предусматривает два формата моментальных снимков: собственный режим bcp и символьный режим. Подписчики, не относящиеся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , требуют использования моментальных снимков символьного формата.  
  
-   Подписчики, не относящиеся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , не могут использовать подписки с немедленным обновлением или обновлением посредством очередей и не могут быть узлами одноранговой топологии.  
  
-   Подписчики, не относящиеся к[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , не могут быть автоматически инициализированы из резервной копии.  
  
## <a name="see-also"></a>См. также  
 [Разнородная репликация базы данных](heterogeneous-database-replication.md)   
 [Подписка на публикации](../subscribe-to-publications.md)  
  
  

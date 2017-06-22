---
title: "Настройка производительности для издателей Oracle | Документация Майкрософт"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Oracle publishing [SQL Server replication], performance tuning
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
caps.latest.revision: 34
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 43042f93e80be4f9bf7c5044cc11791c614d85f0
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="performance-tuning-for-oracle-publishers"></a>Настройка производительности для издателей Oracle
  Архитектура публикации Oracle аналогична архитектуре публикации [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] , поэтому первый шаг в настройке производительности репликации Oracle состоит в выполнении следующих общих рекомендаций по настройке, описанных в статье [Enhance General Replication Performance](../../../relational-databases/replication/administration/enhance-general-replication-performance.md).  
  
 Помимо этого, существуют еще две настройки для издателей Oracle, относящиеся к производительности:  
  
-   Указание соответствующего параметра публикации: Oracle или Oracle Gateway.  
  
-   Настройка задания наборов транзакций для обработки изменений на издателе в соответствующие интервалы.  
  
## <a name="specifying-the-appropriate-publishing-option"></a>Указание соответствующего параметра публикации  
 Параметр Oracle Gateway обеспечивает большую производительность по сравнению с параметром Oracle Complete. Тем не менее этот параметр нельзя использовать для публикации одной и той же таблицы в нескольких публикациях транзакций. Таблица может присутствовать только в одной публикации транзакций и в любом количестве публикаций моментальных снимков. Если необходимо опубликовать одну таблицу в нескольких публикациях транзакций, выберите параметр Oracle Complete. Укажите этот параметр при идентификации издателя Oracle на распространителе [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] . Дополнительные сведения см. в разделе [Create a Publication from an Oracle Database](../../../relational-databases/replication/publish/create-a-publication-from-an-oracle-database.md).  
  
## <a name="configuring-the-transaction-set-job"></a>Настройка задания наборов транзакций  
 Изменения в публикуемых таблицах Oracle обрабатываются группами, называемыми наборами транзакций. Для обеспечения согласованности транзакций каждый набор транзакций фиксируется в базе данных распространителя как одна транзакция. Если набор транзакций становится слишком большим, то его невозможно эффективно обработать как одну транзакцию.  
  
 По умолчанию наборы транзакций создаются только агентом чтения журнала. Если во время периодов с большим количеством изменений агент чтения журнала не запущен или не может подключиться к распространителю [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] с издателем Oracle, то наборы транзакций могут стать слишком большими, чтобы ими можно было управлять. Во избежание этой проблемы нужно обеспечить создание наборов транзакций через постоянные интервалы, даже если агент чтения журнала не запущен или не может соединиться с издателем Oracle.  
  
 Наборы транзакций могут создаваться заданием набора транзакций (заданием базы данных Oracle, устанавливаемым репликацией), использующим механизм, аналогичный тому, который использует агент чтения журнала для создания наборов. При каждом запуске задания создается новый набор транзакций. При следующем запуске агента чтения журнала он обрабатывает все созданные наборы. Если после обработки всех существующих наборов транзакций остаются незаконченные изменения, то агент чтения журнала создает и обрабатывает один или несколько дополнительных наборов транзакций.  
  
 Настройка задания набора транзакций описана в статье [Настройка задания для набора транзакций в издателе Oracle (программирование репликации на языке Transact-SQL)](../../../relational-databases/replication/administration/configure-the-transaction-set-job-for-an-oracle-publisher.md).  
  
## <a name="see-also"></a>См. также:  
 [Настройка издателя Oracle](../../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md)   
 [Oracle Publishing Overview](../../../relational-databases/replication/non-sql/oracle-publishing-overview.md)  
  
  

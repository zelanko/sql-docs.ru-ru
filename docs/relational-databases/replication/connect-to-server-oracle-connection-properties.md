---
title: "Соединение с сервером Oracle (страница \"Свойства соединения\") | Документация Майкрософт"
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
f1_keywords: sql13.rep.oracleconnection.connectionprops.f1
helpviewer_keywords: Connect to Server dialog box, replication
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
caps.latest.revision: "16"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: fbf8a1d214a50d809275af775900681c61f613be
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/18/2018
---
# <a name="connect-to-server-oracle-connection-properties"></a>Соединение с сервером (Oracle), свойства соединения
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Вкладка **Свойства соединения** диалогового окна **Соединение с сервером** позволяет задать параметр публикации **Шлюз** или **Полный**. После идентификации издателя изменить данный параметр без удаления и перенастройки издателя невозможно. Дополнительные сведения см. в статье [Настройка издателя Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## <a name="options"></a>Параметры  
 **Тип издателя**  
 Выберите **Шлюз** или **Полный**. Параметр **Полный** обеспечивает публикации моментальных снимков и транзакций полным набором поддерживаемых функций, необходимых для публикаций Oracle. Параметр **Шлюз** оптимизирует работу системы для случаев, когда шлюзом между системами выступает репликация. Параметр **Шлюз** нельзя использовать, если одна и та же таблица будет публиковаться в нескольких публикациях транзакций. Если выбран параметр **Шлюз**, то таблица может использоваться только в одной публикации транзакций и в любом количестве публикаций моментальных снимков.  
  
 **Время ожидания**  
 Указывает, как долго распространитель [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] должен пытаться подключиться к издателю Oracle, прежде чем выдать ошибку времени ожидания.  
  
## <a name="see-also"></a>См. также:  
 [Глоссарий терминов по публикации Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Performance Tuning for Oracle Publishers](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  

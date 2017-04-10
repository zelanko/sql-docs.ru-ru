---
title: "Соединение с сервером (Oracle), свойства соединения | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.oracleconnection.connectionprops.f1"
helpviewer_keywords: 
  - "Диалоговое окно "Соединение с сервером", репликация"
ms.assetid: 1bb7396f-cbb2-4f88-b82b-543287ed4172
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# Соединение с сервером (Oracle), свойства соединения
  Вкладка **Свойства соединения** диалогового окна **Соединение с сервером** позволяет задать параметры публикации **Шлюз** или **Полный**. После идентификации издателя изменить данный параметр без удаления и перенастройки издателя невозможно. Дополнительные сведения см. в разделе [настроить издатель Oracle](../../relational-databases/replication/non-sql/configure-an-oracle-publisher.md).  
  
## Параметры  
 **Тип издателя**  
 Выберите **шлюза** или **завершения**. Параметр **Полный** обеспечивает публикации моментальных снимков и транзакций с полным набором поддерживаемых функций для публикаций Oracle. Параметр **Шлюз** оптимизирует работу системы для случаев, когда в качестве шлюза между системами выступает репликация. Параметр **Шлюз** нельзя использовать, если одна и та же таблица будет публиковаться в нескольких публикациях транзакций. Если выбран параметр **Шлюз**, то таблица может использоваться только в одной публикации транзакций и в любом количестве публикаций моментальных снимков.  
  
 **Время ожидания**  
 Указать, как долго [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] распространителя пытаться подключиться к издателю Oracle, до возникновения ошибки времени ожидания.  
  
## См. также:  
 [Глоссарий терминов публикации Oracle](../../relational-databases/replication/non-sql/glossary-of-terms-for-oracle-publishing.md)   
 [Настройка производительности для издателей Oracle](../../relational-databases/replication/non-sql/performance-tuning-for-oracle-publishers.md)  
  
  
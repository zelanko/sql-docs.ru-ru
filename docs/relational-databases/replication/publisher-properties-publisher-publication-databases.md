---
title: "Свойства издателя — издатель, базы данных публикации | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.configdistwizard.pubproperties.pubdb.f1"
helpviewer_keywords: 
  - "Диалоговое окно «Свойства издателя»"
ms.assetid: 574ea2e7-4e7b-4733-ab52-429ca93c7b0a
caps.latest.revision: 21
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 21
---
# Свойства издателя — издатель, базы данных публикации
  Страница **Базы данных публикации** диалогового окна **Свойства издателя** позволяет пользователю в предопределенной роли сервера **sysadmin** включить базы данных для репликации. Включение базы данных не ее публикации. Вместо этого оно позволяет любому пользователю **db_owner** фиксированной роли базы данных для этой базы данных создать одну или несколько публикаций в базе данных.  
  
## Параметры  
 **Транзакционная**  
 Установите этот флажок, чтобы разрешить пользователям в **db_owner** фиксированной роли базы данных для создания публикации моментальных снимков или публикации транзакций в базе данных.  
  
 **Объединить**  
 Установите этот флажок, чтобы разрешить пользователям в **db_owner** фиксированной роли базы данных могли создавать публикации слиянием в базе данных.  
  
## См. также:  
 [Просмотр и изменение свойств издателя и распространителя](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md)   
 [Справочник по свойствам & #40; Репликация & #41;](../../relational-databases/replication/properties-reference-replication.md)  
  
  
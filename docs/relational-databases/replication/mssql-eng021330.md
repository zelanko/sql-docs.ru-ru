---
title: "MSSQL_ENG021330 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG021330, ошибка"
ms.assetid: e2bb2e21-62a7-4689-b68b-bdfba3fdd985
caps.latest.revision: 16
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 16
---
# MSSQL_ENG021330
    
## Сведения о сообщении  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|21330|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Не удалось создать вложенный каталог в рабочем каталоге репликации.(%ls)|  
  
## Объяснение  
 Эта ошибка может произойти при ручной инициализации подписки, существует ошибка при создании каталога, в котором хранятся скрипты репликации. Ошибка может быть вызвана недостатком разрешений: если инициализация подписки выполняется без применения моментального снимка, то учетная запись, от имени которой выполняется служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] на издателе, должна обладать разрешением на запись в папку моментальных снимков распространителя.  
  
## Действие пользователя  
 Проверьте правильность указанного пути к папке моментальных снимков, а также убедитесь, что учетная запись, под которой работает служба [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] издателя, обладает всеми необходимыми разрешениями.  
  
## См. также:  
 [Укажите местоположение моментальных снимков по умолчанию & #40; SQL Server Management Studio & #41;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Ошибки и события ссылку & #40; Репликация & #41;](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [Инициализация подписки на публикацию транзакций без моментального снимка](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  
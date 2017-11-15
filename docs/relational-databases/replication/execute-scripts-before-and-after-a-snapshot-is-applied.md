---
title: "Выполнение скриптов до и после применения моментального снимка | Документация Майкрософт"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- snapshots [SQL Server replication], scripts
- scripts [SQL Server replication], snapshots
- snapshot replication [SQL Server], scripts
ms.assetid: b7bb1e4c-5b48-4bb1-9dc8-47c911f2cc82
caps.latest.revision: "39"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: d55cdb641ce0048bf959a530988edf92cbe63155
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="execute-scripts-before-and-after-a-snapshot-is-applied"></a>Выполнение скриптов до и после применения моментального снимка
  Указать дополнительный скрипт для выполнения до или после применения моментального снимка можно на странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>**. Дополнительные сведения о доступе к этому диалоговому окну см. в разделе [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
> [!NOTE]  
>  Эти параметры недоступны, если параметр **Формат моментального снимка** установлен в **Символьный**.  
  
### <a name="to-execute-a-script-before-or-after-a-snapshot-is-applied"></a>Выполнение скрипта до или после применения моментального снимка  
  
1.  На странице **Моментальный снимок** диалогового окна **Свойства публикации — \<публикация>** сделайте следующее:  
  
    -   Чтобы указать скрипт для выполнения до применения моментального снимка, щелкните **Обзор** для перехода к скрипту или введите путь к скрипту в текстовом поле **Перед применением моментального снимка выполнить этот скрипт** .  
  
        > [!NOTE]  
        >  У агента распространителя или агента слияния должны быть разрешения на чтение в указанном каталоге. Если используются подписки по запросу, следует указать общий каталог в формате UNC-пути, например \\\computername\scripts\myscript.sql.  
  
    -   Чтобы указать скрипт для выполнения после применения моментального снимка, щелкните **Обзор** для перехода к скрипту или введите путь к скрипту в текстовом поле **После применения моментального снимка выполнить этот скрипт** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>См. также:  
 [Настройка свойств моментального снимка (программирование репликации на языке Transact-SQL)](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Изменение свойств публикации и статьи](../../relational-databases/replication/publish/change-publication-and-article-properties.md)   
 [Выполнение скриптов до и после применения моментального снимка](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md)   
 [Инициализация подписки с помощью моментального снимка](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  

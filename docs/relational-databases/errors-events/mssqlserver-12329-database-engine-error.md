---
title: "MSSQLSERVER_12329 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
caps.latest.revision: 4
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 47b2380fdb3bf5fbde95bfbd984c3ed6095dcd1f
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver12329"></a>MSSQLSERVER_12329
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|12329|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_UNSUPPORTED_NON_LATIN_CODEPAGE|  
|Текст сообщения|Типы данных char(n) и varchar(n) с параметрами сортировки, кодовая страница которых отлична от 1252, не поддерживаются *конструкцией*.|  
  
## <a name="explanation"></a>Объяснение  
Не используйте типы данных char(n) и varchar(n) с параметрами сортировки, кодовая страница которых отлична от 1252.  
  
## <a name="user-action"></a>Действие пользователя  
Одна непредвиденная ситуация, которая может привести к формированию этой ошибки:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
Вместо этого используйте:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  


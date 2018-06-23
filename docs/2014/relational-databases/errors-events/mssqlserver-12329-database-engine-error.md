---
title: MSSQLSERVER_12329 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
caps.latest.revision: 5
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 01d7f8f0f7833b3ef6c5fb5c87777bb6461d3b41
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36192899"
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
  
  
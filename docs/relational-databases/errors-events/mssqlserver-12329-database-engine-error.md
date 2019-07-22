---
title: MSSQLSERVER_12329 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 404f414a1f4bfe75c3476e0954e810c4b36ddaa3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68002899"
---
# <a name="mssqlserver12329"></a>MSSQLSERVER_12329
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  

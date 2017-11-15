---
title: "MSSQLSERVER_2508 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 84b5e10c6a26536153bafceede732c5d2fd56618
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver2508"></a>MSSQLSERVER_2508
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2508|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|Текст сообщения|Подсчет %.*ls для объекта "%.\*ls", идентификатора индекса %d, идентификатора секции %I64d, идентификатора единицы размещения %I64d (тип %.\*ls) неверен. Запустите команду DBCC UPDATEUSAGE.|  
  
## <a name="explanation"></a>Объяснение  
В версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующих версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], значения количества строк таблиц и индексов, а также количества страниц могут стать неверными. Базы данных, которые были созданы с помощью версий, предшествующих [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], могут содержать неверные подсчеты. Команда DBCC CHECKDB была улучшена, чтобы обнаруживать эти ошибки и возвращать предупреждающие сообщения.  
  
## <a name="user-action"></a>Действие пользователя  
Запустите команду DBCC UPDATEUSAGE для указанного объекта или индекса, или для базы данных, в которой содержится объект, чтобы исправить недопустимые подсчеты.  
  

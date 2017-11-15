---
title: "MSSQLSERVER_10737 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 10737 (Database Engine error)
ms.assetid: 208af6ed-b271-4ab8-803e-7666025385c8
caps.latest.revision: "10"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: a5fef9ff1b72130ae5cb935a27e5ad82fc616d66
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver10737"></a>MSSQLSERVER_10737
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|10737|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REBUILD_PARTITION_ALL_NOT_SPECIFIED|  
|Текст сообщения|Если в предложении DATA_COMPRESSION инструкции ALTER TABLE REBUILD или ALTER INDEX REBUILD указана секция, то должно быть задано предложение PARTITION=ALL. Предложение PARTITION=ALL используется для подтверждения того, что должны быть перестроены все секции таблицы или индекса, даже если в предложении DATA_COMPRESSION указано только подмножество.|  
  
## <a name="user-action"></a>Действие пользователя  
Добавьте предложение PARTITION=ALL к инструкции ALTER INDEX или ALTER TABLE. Также вы можете перестроить конкретную секцию, используя команду REBUILD PARTITION = \<выражение_номера_секции> WITH (DATA_COMPRESSION={ON | OFF}).  
  

---
title: "MSSQLSERVER_3417 | Документация Майкрософт"
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
- 3417 (Database Engine error)
ms.assetid: 005829c8-cf57-4828-818a-bbe8ee2e00f0
caps.latest.revision: 17
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: a24a6c95f5ccd79fe4eb3af627be689755469a56
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver3417"></a>MSSQLSERVER_3417
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|3417|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|REC_BADMASTER|  
|Текст сообщения|Невозможно восстановить базу данных master. Не удалось запустить SQL Server. Восстановите базу данных master из полной резервной копии, исправьте ее или перестройте. Дополнительные сведения о перестроении базы данных master см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
SQL Server не может запустить базу данных **master**. Если базы данных **master** или **tempdb** не могут быть переведены в оперативный режим, то SQL Server запустить нельзя. Эта ошибка обычно предшествует другим ошибкам. Чтобы найти источник ошибки, просмотрите журнал ошибок.  
  
## <a name="user-action"></a>Действие пользователя  
Восстановите базу данных из резервной копии или исправьте ее.  
  


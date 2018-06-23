---
title: MSSQLSERVER_360 | Документация Майкрософт
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
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
caps.latest.revision: 11
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2300cb7f2e45ca9ab76b9c8b7da23e5cb59e364c
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36095937"
---
# <a name="mssqlserver360"></a>MSSQLSERVER_360
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|360|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DML_UPDATE_SPARSE_AND_COLSET|  
|Текст сообщения|Список целевых столбцов для инструкций INSERT, UPDATE или MERGE не может содержать одновременно разреженный столбец и набор столбцов, в состав которого входит разреженный столбец. Перепишите запрос таким образом, чтобы список целевых столбцов содержал либо разреженный столбец, либо набор столбцов, но не то и другое сразу.|  
  
## <a name="explanation"></a>Объяснение  
 Набор столбцов представляет собой нетипизированное XML-представление, объединяющее несколько столбцов таблицы в виде структурированного вывода. Была предпринята попытка изменить набор столбцов и столбец, являющийся частью набора столбцов, в результате чего были созданы две ссылки на один и тот же столбец.  
  
## <a name="user-action"></a>Действие пользователя  
 Перепишите инструкцию таким образом, чтобы в ней содержалась ссылка либо на столбец, либо на набор столбцов, но не на то и другое одновременно.  
  
  
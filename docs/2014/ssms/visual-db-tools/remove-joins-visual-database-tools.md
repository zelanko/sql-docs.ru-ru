---
title: Удаление соединений (визуальные инструменты для баз данных) | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- removing joins
- joins [SQL Server], removing
- deleting joins
ms.assetid: ccc212a1-fd13-48d6-85e5-5ff310c34bbd
caps.latest.revision: 10
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4a9bcc6fa9915635b2bc7c7bffb98e85a4f021de
ms.sourcegitcommit: 8ae6e6618a7e9186aab3c6a37ea43776aa9a382b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "43809240"
---
# <a name="remove-joins-visual-database-tools"></a>Удаление соединений (визуальные инструменты для баз данных)
  Если нежелательно, чтобы таблицы были соединены с помощью внутреннего или внешнего соединения, можно удалить это соединение между таблицами. Например, можно удалить соединение, автоматически созданное между двумя таблицами в [конструкторе запросов и представлений](visual-database-tools.md) .  
  
> [!NOTE]  
>  Удаление соединения из запроса не влияет на базовые связи, существующие в базе данных.  
  
 Если две соединяемые таблицы являются частью запроса и все условия соединения между ними удаляются, то результирующий запрос становится пересечением этих таблиц, то есть перекрестным соединением (CROSS JOIN).  
  
### <a name="to-remove-a-join"></a>Удаление соединения  
  
-   На [панели диаграммы](diagram-pane-visual-database-tools.md)выберите удаляемую линию соединения и нажмите клавишу DELETE. Можно одновременно выбрать и удалить несколько линий соединений.  
  
 Конструктор запросов и представлений удаляет линию соединения и изменяет инструкцию на [панели SQL](sql-pane-visual-database-tools.md).  
  
## <a name="see-also"></a>См. также  
 [Автоматическое соединение таблиц &#40;визуальных инструментах баз данных&#41;](join-tables-automatically-visual-database-tools.md)   
 [Соединение таблиц вручную &#40;визуальных инструментах баз данных&#41;](join-tables-manually-visual-database-tools.md)   
 [Запросы с соединениями (визуальные инструменты для баз данных)](query-with-joins-visual-database-tools.md)  
  
  

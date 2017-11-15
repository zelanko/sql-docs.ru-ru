---
title: "MSSQLSERVER_1101 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1101 (Database Engine error)
ms.assetid: d63b67d5-59f5-4f77-904e-5ba67f2dd850
caps.latest.revision: "18"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: e5928760fba84d8a2a7da76ef15026d7a0df4a36
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver1101"></a>MSSQLSERVER_1101
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1101|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NOALLOCPG|  
|Текст сообщения|Не удалось выделить новую страницу для базы данных "%.*ls" вследствие нехватки места на диске в файловой группе "%.\*ls". Предоставьте необходимое место на диске, удалив объекты в файловой группе, добавив дополнительные файлы в файловую группу или указав параметр автоматического увеличения размера для существующих файлов в файловой группе.|  
  
## <a name="explanation"></a>Объяснение  
Нет свободного места на диске в файловой группе.  
  
## <a name="user-action"></a>Действие пользователя  
Место в файловой группе можно освободить следующим образом.  
  
-   Включить автоматическое расширение.  
  
-   Добавить файлы в файловую группу.  
  
-   Освободить место на диске, удалив ненужные индексы или таблицы из файловой группы.  
  

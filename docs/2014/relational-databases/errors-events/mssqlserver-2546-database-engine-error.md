---
title: MSSQLSERVER_2546 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: ca1a8af843d0183acd46a8b11e00427738d59d0e
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2020
ms.locfileid: "62868855"
---
# <a name="mssqlserver_2546"></a>MSSQLSERVER_2546
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2546|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_INDEX_MARKED_DISABLED|  
|Текст сообщения|Индекс «INDEX_NAME» для таблицы «OBJECT_NAME» помечен как отключенный. Перестройте индекс и переведите его в режим «в сети».|  
  
## <a name="explanation"></a>Объяснение  
 Указанный индекс помечен как находящийся в режиме «вне сети» или как отключенный. Таким образом, данный индекс не может быть проверен.  
  
## <a name="user-action"></a>Действие пользователя  
 Перестройте индекс с помощью оператора ALTER INDEX.  
  
## <a name="see-also"></a>См. также:  
 [Инструкция ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql)   
 [Реорганизация и перестроение индексов](../indexes/indexes.md)  
  
  

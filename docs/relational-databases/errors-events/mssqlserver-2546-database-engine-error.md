---
description: MSSQLSERVER_2546
title: MSSQLSERVER_2546 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d955e5e7a0ab7ec1bc8c34306bc983683275f05c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482822"
---
# <a name="mssqlserver_2546"></a>MSSQLSERVER_2546
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
[ALTER INDEX (Transact-SQL)](~/t-sql/statements/alter-index-transact-sql.md)  
[Реорганизация и перестроение индексов](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  

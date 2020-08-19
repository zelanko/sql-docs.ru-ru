---
description: MSSQLSERVER_2596
title: MSSQLSERVER_2596 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2596 (Database Engine error)
ms.assetid: 49ab892f-8ba3-4ba1-b562-ddf205019802
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ce3ed3f225671a762ba6e39f958c6347f813076f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88410860"
---
# <a name="mssqlserver_2596"></a>MSSQLSERVER_2596
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|2596|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_DATABASE_IN_READ_ONLY_MODE|  
|Текст сообщения|Инструкция восстановления не была обработана. База данных не может быть доступна только для чтения.|  
  
## <a name="explanation"></a>Объяснение  
Это сообщение указывает, что база данных находится в режиме «только для чтения». Восстановление невозможно, если база данных находится в режиме «только для чтения».  
  
## <a name="user-action"></a>Действие пользователя  
При помощи инструкции ALTER DATABASE переведите базу данных в режим чтения и записи, а затем повторите команду DBCC.  
  
## <a name="see-also"></a>См. также:  
[ALTER DATABASE (Transact-SQL)](~/t-sql/statements/alter-database-transact-sql-set-options.md)  
  

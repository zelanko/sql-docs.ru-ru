---
title: MSSQLSERVER_12301 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 12301 (Database Engine error)
ms.assetid: 69455df4-4ce9-4a6f-af5a-8bbc93e21245
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 203d4bd9f4ba91bf553b869a1103daa430d6812f
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781197"
---
# <a name="mssqlserver_12301"></a>MSSQLSERVER_12301
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|12301|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_UNSUPPORTED_NULLABLE_COLUMNS|  
|Текст сообщения|Столбцы в ключе индекса, допускающие значения NULL, не поддерживаются для "*конструкция*".|  
  
## <a name="user-action"></a>Действие пользователя  
Не используйте столбцы, допускающие значения NULL, в ключе индекса.  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

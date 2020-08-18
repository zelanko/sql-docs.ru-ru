---
description: MSSQLSERVER_12301
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
ms.openlocfilehash: bc924f153aad50b8817b818de18783f4b6cf6b55
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88336060"
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
  

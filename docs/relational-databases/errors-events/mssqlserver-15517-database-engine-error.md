---
title: MSSQLSERVER_15517 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
caps.latest.revision: 5
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: aa40bae852fa2c23df4dd92c7b43aeddf05e1651
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
---
# <a name="mssqlserver15517"></a>MSSQLSERVER_15517
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|15517|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SEC_CANNOTEXECUTEASUSER|  
|Текст сообщения|Невозможно выполнить в качестве участника базы данных, поскольку участник "*участник*" не существует, этот тип участника не может проходить олицетворение или отсутствует разрешение.|  
  
## <a name="user-action"></a>Действие пользователя  
Используйте имя существующего участника или получите разрешение IMPERSONATE для этого участника.  
  
15517 может также возникнуть после присоединения и восстановления базы данных пользователем, который не является ее изначальным владельцем. Чтобы устранить эту ошибку, измените db_owner на имя входа на сервере с помощью следующей команды:  
  
```  
ALTER AUTHORIZATION ON DATABASE:: DBName TO [NewLogin]  
```  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

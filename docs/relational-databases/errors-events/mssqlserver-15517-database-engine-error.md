---
title: "MSSQLSERVER_15517 | Документация Майкрософт"
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
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
caps.latest.revision: 5
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 74535f1684eef8e5dbc9736a1e4a7f6c4b258d5c
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver15517"></a>MSSQLSERVER_15517
  
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
[Выполняющаяся в памяти OLTP &#40;оптимизация в памяти&#41;](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  


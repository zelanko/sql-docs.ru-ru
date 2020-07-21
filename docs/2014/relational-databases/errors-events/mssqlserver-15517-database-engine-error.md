---
title: MSSQLSERVER_15517 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9591bc02f07f3bd29c0a2532942851141732d6a2
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86553773"
---
# <a name="mssqlserver_15517"></a>MSSQLSERVER_15517
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
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
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

---
title: MSSQLSERVER_15517 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15517 (Database Engine error)
ms.assetid: f94287f5-129f-4c52-9d34-62b996088001
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1e0ba7408f4e58cd10693831eb6c4ae1f4c2c35c
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47697862"
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
  

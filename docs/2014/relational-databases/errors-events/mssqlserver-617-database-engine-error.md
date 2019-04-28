---
title: MSSQLSERVER_617 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 617 (Database Engine error)
ms.assetid: 213545d9-08a7-4427-bfd1-8b7e16644281
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f63983243d0859fcb7ebaaf1ac5d184757d1f274
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62867204"
---
# <a name="mssqlserver617"></a>MSSQLSERVER_617
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|617|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|NODESHASH|  
|Текст сообщения|Дескриптор объекта с идентификатором %ld в базе данных с идентификатором %d не обнаружен в хэш-таблице при попытке его восстановления по хэшу. В рабочей таблице отсутствует запись. Повторите запрос. Если используется курсор, закройте и заново откройте его.|  
  
## <a name="explanation"></a>Объяснение  
SQL Server не может найти рабочую таблицу для конкретной записи.  
  
## <a name="user-action"></a>Действие пользователя  
  
1.  Если используется курсор, закройте и заново откройте его.  
  
2.  Повторите запрос.  
  

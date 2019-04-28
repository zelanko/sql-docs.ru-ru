---
title: MSSQLSERVER_17803 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 683806941947a6da888264e4d0e4e3807200ef13
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869549"
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|17803|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_NOMEMORY|  
|Текст сообщения|Во время установления соединения произошла ошибка выделения памяти. Сократите необязательный расход памяти или увеличьте объем системной памяти. Соединение было закрыто.%.*ls|  
  
## <a name="explanation"></a>Объяснение  
Серверу не хватает памяти.  
  
## <a name="user-action"></a>Действие пользователя  
Определите причину нехватки памяти на сервере. Возможно, окажутся полезными общие шаги по устранению неполадок с памятью.  
  

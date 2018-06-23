---
title: MSSQLSERVER_17803 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
caps.latest.revision: 14
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: b7a2ab967786eaa05c8ac393bbeaf0e42164f0f6
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36187768"
---
# <a name="mssqlserver17803"></a>MSSQLSERVER_17803
    
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
  
  
---
title: MSSQLSERVER_8710 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6cf47d5f98420ba49a33d6358ee910a99765d3e8
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34325395"
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|8710|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|QUERY2_CUBE_ILLEGAL_AGG_FUNC|  
|Текст сообщения|Агрегатные функции, используемые в запросах CUBE, ROLLUP или GROUPING SET, должны обеспечивать возможность слияния подытогов. Чтобы решить эту проблему, удалите агрегатную функцию или напишите запрос UNION ALL с предложениями GROUP BY.|  
  
## <a name="explanation"></a>Объяснение  
В запросе CUBE, ROLLUP или GROUPING SETS была использована агрегатная функция, не предусматривающая метод для слияния подытогов.  
  
## <a name="user-action"></a>Действие пользователя  
Чтобы решить эту проблему, удалите агрегатную функцию или напишите запрос UNION ALL с предложениями GROUP BY.  
  

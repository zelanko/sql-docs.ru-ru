---
title: MSSQLSERVER_8710 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 8710 (Database Engine error)
ms.assetid: 78b9f9da-5489-4be0-94df-f065d86ed18c
caps.latest.revision: 8
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b5e484ad03915e46aeac1cf0eb067cb49bc16f8c
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37411293"
---
# <a name="mssqlserver8710"></a>MSSQLSERVER_8710
    
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
  
  

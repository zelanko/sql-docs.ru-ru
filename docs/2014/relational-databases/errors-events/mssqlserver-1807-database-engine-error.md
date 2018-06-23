---
title: MSSQLSERVER_1807 | Документация Майкрософт
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
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 929ea0f5ecda6697b49f3813106cc5766ce8084f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36096448"
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|1807|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|CANNOT_EX_LOCK|  
|Текст сообщения|Не удалось получить монопольную блокировку для базы данных «%.*ls». Повторите операцию позже.|  
  
## <a name="explanation"></a>Объяснение  
 Операция, которой необходима монопольная блокировка базы данных, не смогла получить ее.  
  
## <a name="user-action"></a>Действие пользователя  
 Отключите все соединения с базой данных и повторите запрос.  
  
  
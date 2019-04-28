---
title: MSSQLSERVER_1807 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 69acb74bd1c50900ae4852c41b3304da7ca7c00c
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62869467"
---
# <a name="mssqlserver1807"></a>MSSQLSERVER_1807
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  

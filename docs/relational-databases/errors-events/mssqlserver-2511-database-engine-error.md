---
title: "MSSQLSERVER_2511 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 8b7c7da552aee4357d98e05597bffef3ca5f08ad
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver2511"></a>MSSQLSERVER_2511
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2511|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_KEYS_OUT_OF_ORDER|  
|Текст сообщения|Ошибка таблицы: идентификатор объекта %d, идентификатор индекса %d, идентификатор секции %I64d, идентификатор единицы размещения %I64d (тип %.*ls). Нарушен порядок следования ключей на странице %S_PGID, слоты %d и %d.|  
  
## <a name="explanation"></a>Объяснение  
В указанном индексе были обнаружены неупорядоченные ключи. Страница, на которой содержатся эти ключи, может быть повреждена.  
  
## <a name="user-action"></a>Действие пользователя  
Перестройте указанный индекс с помощью инструкции ALTER INDEX REBUILD.  
  

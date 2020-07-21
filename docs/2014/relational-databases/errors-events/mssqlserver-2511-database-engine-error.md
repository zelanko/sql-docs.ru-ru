---
title: MSSQLSERVER_2511 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: be51c47f9fa8ec4188d13ecfa66441ed262f7e32
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552120"
---
# <a name="mssqlserver_2511"></a>MSSQLSERVER_2511
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2511|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_KEYS_OUT_OF_ORDER|  
|Текст сообщения|Ошибка таблицы: идентификатор объекта %d, идентификатор индекса %d, идентификатор секции %I64d, идентификатор единицы распределения %I64d (тип %.*ls). Нарушен порядок следования ключей на странице %S_PGID, слоты %d и %d.|  
  
## <a name="explanation"></a>Объяснение  
 В указанном индексе были обнаружены неупорядоченные ключи. Страница, на которой содержатся эти ключи, может быть повреждена.  
  
## <a name="user-action"></a>Действие пользователя  
 Перестройте указанный индекс с помощью инструкции ALTER INDEX REBUILD.  
  
  

---
title: MSSQLSERVER_2511 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2511 (Database Engine error)
ms.assetid: 9a00c0ed-eb4b-4fae-8016-192396006c37
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26a6a753942bfb111a5e2b5c6b821577d660cc12
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656752"
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
  

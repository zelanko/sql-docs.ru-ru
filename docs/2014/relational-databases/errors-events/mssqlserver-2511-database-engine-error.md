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
ms.openlocfilehash: 23e91b0d64140329639cf57f3a336cd2eab8e4e8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85034507"
---
# <a name="mssqlserver_2511"></a>MSSQLSERVER_2511
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|2511|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_KEYS_OUT_OF_ORDER|  
|Текст сообщения|Ошибка таблицы: идентификатор объекта %d, идентификатор индекса %d, идентификатор секции %I64d, идентификатор единицы размещения %I64d (тип %.*ls). Нарушен порядок следования ключей на странице %S_PGID, слоты %d и %d.|  
  
## <a name="explanation"></a>Объяснение  
 В указанном индексе были обнаружены неупорядоченные ключи. Страница, на которой содержатся эти ключи, может быть повреждена.  
  
## <a name="user-action"></a>Действие пользователя  
 Перестройте указанный индекс с помощью инструкции ALTER INDEX REBUILD.  
  
  

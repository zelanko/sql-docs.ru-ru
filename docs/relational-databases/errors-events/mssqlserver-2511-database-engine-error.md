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
ms.openlocfilehash: c28be4ae43225cc4593291285c09115829be8da2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85780449"
---
# <a name="mssqlserver_2511"></a>MSSQLSERVER_2511
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  

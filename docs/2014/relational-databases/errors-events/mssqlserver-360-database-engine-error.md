---
title: MSSQLSERVER_360 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 21534d6cd1499634b5d93c7140b4f8f47b3e242b
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551549"
---
# <a name="mssqlserver_360"></a>MSSQLSERVER_360
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|360|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DML_UPDATE_SPARSE_AND_COLSET|  
|Текст сообщения|Список целевых столбцов для инструкций INSERT, UPDATE или MERGE не может содержать одновременно разреженный столбец и набор столбцов, в состав которого входит разреженный столбец. Перепишите запрос таким образом, чтобы список целевых столбцов содержал либо разреженный столбец, либо набор столбцов, но не то и другое сразу.|  
  
## <a name="explanation"></a>Объяснение  
 Набор столбцов представляет собой нетипизированное XML-представление, объединяющее несколько столбцов таблицы в виде структурированного вывода. Была предпринята попытка изменить набор столбцов и столбец, являющийся частью набора столбцов, в результате чего были созданы две ссылки на один и тот же столбец.  
  
## <a name="user-action"></a>Действие пользователя  
 Перепишите инструкцию таким образом, чтобы в ней содержалась ссылка либо на столбец, либо на набор столбцов, но не на то и другое одновременно.  
  
  

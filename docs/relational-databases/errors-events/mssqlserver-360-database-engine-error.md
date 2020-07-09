---
title: MSSQLSERVER_360 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 360 (Database Engine error)
ms.assetid: e2b7c1b2-3679-4206-9b25-6bd55ef96a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ad12a38d7921ba2c10a4b044ca85035646db171
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85723442"
---
# <a name="mssqlserver_360"></a>MSSQLSERVER_360
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  

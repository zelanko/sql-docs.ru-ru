---
title: "MSSQLSERVER_ 9532 | Документация Майкрософт"
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
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 514c8efd47a7cb54397db495a268b1c9c415be58
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver9532"></a>MSSQLSERVER_9532
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9532|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|XMLERR_COLUMNSET_CANNOT_CONVERT_FROM_TO|  
|Текст сообщения|При обработке запроса или операции DML над набором столбцов "%.*ls" произошла ошибка преобразования данных типа "%ls" к типу "%ls" для столбца "%.\*ls".|  
  
## <a name="explanation"></a>Объяснение  
Набор столбцов представляет собой нетипизированное XML-представление, объединяющее несколько столбцов таблицы в виде структурированного вывода. При вставке или обновлении значений разреженного столбца в наборе XML-столбцов значения, вставляемые в базовые разреженные столбцы, неявным образом преобразуются из типа данных **xml**. Было передано значение, которое не может быть преобразовано в тип данных столбца.  
  
## <a name="user-action"></a>Действие пользователя  
Поскольку предоставленное значение не удалось неявно преобразовать, запись может оказаться недопустимой. Исправьте ошибку и повторите попытку. Если значение является верным, измените инструкцию таким образом, чтобы использовались отдельные столбцы, а не набор столбцов. Это позволит выполнить приведение значения в правильный тип данных явным образом.  
  

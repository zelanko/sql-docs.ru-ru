---
title: MSSQLSERVER_ 9532 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: 10
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3a54d27a7548bb8988dc0006d62f1e1cd3332ace
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415213"
---
# <a name="mssqlserver9532"></a>MSSQLSERVER_9532
    
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
 Набор столбцов представляет собой нетипизированное XML-представление, объединяющее несколько столбцов таблицы в виде структурированного вывода. При вставке или обновлении значений разреженного столбца в наборе XML-столбцов значения, вставляемые в базовые разреженные столбцы, неявным образом преобразуются из типа данных `xml`. Было передано значение, которое не может быть преобразовано в тип данных столбца.  
  
## <a name="user-action"></a>Действие пользователя  
 Поскольку предоставленное значение не удалось неявно преобразовать, запись может оказаться недопустимой. Исправьте ошибку и повторите попытку. Если значение является верным, измените инструкцию таким образом, чтобы использовались отдельные столбцы, а не набор столбцов. Это позволит выполнить приведение значения в правильный тип данных явным образом.  
  
  

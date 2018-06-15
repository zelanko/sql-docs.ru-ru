---
title: MSSQLSERVER_ 9532 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.suite: sql
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: language-reference
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
caps.latest.revision: 9
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e779b0f514ed6892d345c2f72ecf37b8711257e3
ms.sourcegitcommit: ee661730fb695774b9c483c3dd0a6c314e17ddf8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/19/2018
ms.locfileid: "34329625"
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
  

---
title: MSSQLSERVER_ 9532 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9532 (Database Engine error)
ms.assetid: ab95cce8-4f97-4aea-a746-a73eea7c9aab
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e14c046d646aedbf95a7c7649f6294fc76340994
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47709352"
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
  

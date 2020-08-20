---
description: MSSQL_ENG020574
title: MSSQL_ENG020574 | Документация Майкрософт
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- MSSQL_ENG02574 error
ms.assetid: 4e98f8de-287c-4090-81ee-dc8f80dfa6a1
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 49a12b3b561006196118e7e9aab3d6fecf57779b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88465173"
---
# <a name="mssql_eng020574"></a>MSSQL_ENG020574
[!INCLUDE [SQL Server SQL MI](../../includes/applies-to-version/sql-asdbmi.md)]
    
## <a name="message-details"></a>Сведения о сообщении  
  
|attribute|Значение|  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|20574|  
|Источник события|MSSQLSERVER|  
|Компонент|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|Символическое имя||  
|Текст сообщения|Ошибка проверки данных подписки подписчика "%s" на статью "%s" в публикации "%s".|  
  
## <a name="explanation"></a>Объяснение  
 Было проверено соответствие данных на подписчике данным на издателе, данные не совпали; таким образом, проверка завершилась неуспешно. Дополнительные сведения о проверке см. в разделе [Validate Replicated Data](../../relational-databases/replication/validate-data-at-the-subscriber.md).  
  
## <a name="user-action"></a>Действие пользователя  
 Таким образом, мы рекомендуем сделать следующее:  
  
-   Определите причину ошибки проверки.  
  
-   Исправьте основную проблему, вызвавшую ошибку.  
  
-   Устраните конвергенцию данных, повторно инициализировав подписку или применив другой способ.  
  
## <a name="see-also"></a>См. также:  
 [Справочник по ошибкам и событиям (репликация)](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

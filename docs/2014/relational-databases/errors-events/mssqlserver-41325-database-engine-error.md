---
title: MSSQLSERVER_41325 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41325 (Database Engine error)
ms.assetid: 97c6a8bb-139a-44f3-9ed5-f46d047e8ed3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: a79a8c63fa20aba4d1e64c8e8222b4899e5cb050
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/21/2020
ms.locfileid: "86551439"
---
# <a name="mssqlserver_41325"></a>MSSQLSERVER_41325
    
## <a name="details"></a>Сведения  
  
|attribute|Значение|  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41325|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_TX_COMMIT_SR_VALIDATION|  
|Текст сообщения|Текущей транзакции не удалось выполнить фиксацию из-за ошибки сериализуемой проверки.|  
  
## <a name="explanation"></a>Объяснение  
 В ходе транзакции произошла ошибка проверки, поэтому транзакция завершается.  
  
## <a name="user-action"></a>Действие пользователя  
 Повторите поврежденную транзакцию. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

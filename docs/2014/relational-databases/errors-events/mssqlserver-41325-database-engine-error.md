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
ms.openlocfilehash: 7fc69e5bb311e45c87f474cae23377746399eee7
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85033036"
---
# <a name="mssqlserver_41325"></a>MSSQLSERVER_41325
    
## <a name="details"></a>Сведения  
  
|||  
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
  
  

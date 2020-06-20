---
title: MSSQLSERVER_41359 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 54f17893ef51b97ab88ecc3755447d7018a140b4
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/18/2020
ms.locfileid: "85053937"
---
# <a name="mssqlserver_41359"></a>MSSQLSERVER_41359
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41359|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Текст сообщения|Запрос, который обращается к оптимизированной для памяти таблице с использованием уровня изоляции READ COMMITTED, не может обратиться к дисковой таблице, если для параметра базы данных READ_COMMITTED_SNAPSHOT установлено значение ON. Обеспечьте поддерживаемый уровень изоляции для оптимизированной для памяти таблицы с помощью табличного указания, например WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Объяснение  
 База данных с параметром READ_COMMITTED_SNAPSHOT=ON не поддерживает транзакции, требующие доступа и к таблицам, оптимизированным для памяти, и к дисковым таблицам.  
  
## <a name="user-action"></a>Действие пользователя  
 Установите для параметра READ_COMMITTED_SNAPSHOT значение OFF или укажите поддерживаемый уровень изоляции для оптимизированной для памяти таблицы с помощью табличного указания, например WITH (SNAPSHOT). Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

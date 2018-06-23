---
title: MSSQLSERVER_41396 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
caps.latest.revision: 8
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ea091a41e23c553c273dd9005c19dab8d4e0fb50
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36102193"
---
# <a name="mssqlserver41396"></a>MSSQLSERVER_41396
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41396|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|MAX_SORT_ROWS_EXCEEDED|  
|Текст сообщения|Операция сортировки превысила предел буфера. Выполнение хранимой процедуры было прервано. Дополнительные сведения см. в электронной документации по SQL Server.|  
  
## <a name="explanation"></a>Объяснение  
 Изначально скомпилированные хранимые процедуры выполняют операции сортировки в памяти. Существуют ограничения на размер буфера сортировки. Эта ошибка означает, что размер буфера сортировки превышает это ограничение. Операция сортировки и выполнение хранимой процедуры прерываются.  
  
 Размер каждой строки или записи в буфере сортировки определяется числом отсортированных строк, а также количеством соединений и количеством и типом агрегатных функций в запросе. За счет упрощения запроса можно уменьшить размер каждой строки, таким образом уместив больше строк в буфере сортировки. Размер строк в базовых таблицах не влияет на размер каждой строки или записи в буфере сортировки.  
  
## <a name="user-action"></a>Действие пользователя  
 Выберите меньшее количество строк или уменьшите сложность запроса путем удаления соединений или агрегатных функций.  
  
## <a name="see-also"></a>См. также  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
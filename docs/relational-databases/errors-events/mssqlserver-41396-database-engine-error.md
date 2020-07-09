---
title: MSSQLSERVER_41396 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41396 (Database Engine error)
ms.assetid: 4ff04042-8367-46f3-8a16-c94682d6eedb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6bfaeaa3f9a33e1ae10fbe143df963d8eb9b13b2
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85715472"
---
# <a name="mssqlserver_41396"></a>MSSQLSERVER_41396
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
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
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

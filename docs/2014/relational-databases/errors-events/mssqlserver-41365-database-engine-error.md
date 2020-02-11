---
title: MSSQLSERVER_41365 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dbf921e280b7b01685bb2d4817975149864614a0
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2020
ms.locfileid: "62867945"
---
# <a name="mssqlserver_41365"></a>MSSQLSERVER_41365
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41365|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_MERGE_SCHEDULE_ERROR|  
|Текст сообщения|Запрос на слияние диапазона для транзакции [%ld, %ld] в базе данных %.*ls не был поставлен в расписание. Представляющие диапазон файлы контрольных точек недоступны для слияния либо входят в уже выполняемое слияние.|  
  
## <a name="explanation"></a>Объяснение  
 Представляющие диапазон файлы контрольных точек недоступны для слияния либо входят в уже выполняемое слияние.  
  
## <a name="user-action"></a>Действие пользователя  
 Укажите более подходящий диапазон транзакции для слияния или подождите, а потом еще раз выполните тот же запрос. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
 [Выполняющаяся в памяти OLTP (оптимизация в памяти)](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  

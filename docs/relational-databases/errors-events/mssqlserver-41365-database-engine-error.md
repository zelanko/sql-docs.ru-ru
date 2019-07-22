---
title: MSSQLSERVER_41365 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41365 (Database Engine error)
ms.assetid: 4fc7ec15-b722-4e3d-b7f9-3d39d171e96e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0844bcea9213a3f9272389ee9233ef1becdcd5ff
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68123173"
---
# <a name="mssqlserver41365"></a>MSSQLSERVER_41365
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
Укажите более подходящий диапазон транзакции для слияния или подождите, а потом еще раз выполните тот же запрос. Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

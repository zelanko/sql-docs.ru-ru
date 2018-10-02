---
title: MSSQLSERVER_41342 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41342 (Database Engine error)
ms.assetid: 28270d98-c543-4e7d-b40c-2200e38dce1c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e2e8136363205cf06a210f8a741ed8eb8debaaeb
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47673593"
---
# <a name="mssqlserver41342"></a>MSSQLSERVER_41342
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41342|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_HW_NOT_SUPPORTED|  
|Текст сообщения|Модель процессора в системе не поддерживает создание *конструкция*. Эта ошибка обычно возникает со старыми процессорами.|  
  
## <a name="explanation"></a>Объяснение  
Для оптимизированных для памяти таблиц требуется модель процессора, которая поддерживает операции сравнения и обмена с 128-разрядными значениями, для чего требуется инструкция сборки CMPXCHG16B. Некоторые старые модели процессоров AMD не поддерживают инструкцию CMPXCHG16B. Кроме того, некоторые среды виртуализации не включают эту инструкцию по умолчанию.  
  
## <a name="user-action"></a>Действие пользователя  
Обновите процессор. Если процессор поддерживает инструкцию, а SQL Server выполняется в виртуальной машине, измените конфигурацию, чтобы включить поддержку инструкции CMPXCHG16B.  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

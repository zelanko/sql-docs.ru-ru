---
title: MSSQLSERVER_12304 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 12304 (Database Engine error)
ms.assetid: a2c252c2-e815-4ac8-a101-7af5b32e3233
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 563f4e074cd8c30fa794847a3f0f950f17ce6b19
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781173"
---
# <a name="mssqlserver_12304"></a>MSSQLSERVER_12304
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|12304|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|HK_UNSUPPORTED_IDENTITY_TABLE_VAR|  
|Текст сообщения|Использование табличного типа, оптимизированного для памяти, который использует свойство IDENTITY не поддерживается с любым из его столбцов при использовании типа вне контекста изначально компилированной хранимой процедуры.|  
  
## <a name="user-action"></a>Действие пользователя  
Не используйте тип памяти, оптимизированный для памяти, который использует свойство IDENTITY с любым из его столбцов.  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

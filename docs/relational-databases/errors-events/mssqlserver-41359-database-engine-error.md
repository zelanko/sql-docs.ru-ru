---
description: MSSQLSERVER_41359
title: MSSQLSERVER_41359 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41359 (Database Engine error)
ms.assetid: 02b717c7-9170-4676-b0f6-4dec9eb5b5d4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5de7dc505b2c9ab2c56a4f830dd456acf988f00a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88424336"
---
# <a name="mssqlserver_41359"></a>MSSQLSERVER_41359
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|41359|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQL_READ_COMMITTED_SNAPSHOT_NOT_SUPPORTED|  
|Текст сообщения|Запрос, который обращается к оптимизированной для памяти таблице с использованием уровня изоляции READ COMMITTED, не может обратиться к дисковой таблице, если для параметра базы данных READ_COMMITTED_SNAPSHOT установлено значение ON. Обеспечьте поддерживаемый уровень изоляции для оптимизированной для памяти таблицы с помощью табличного указания, например WITH (SNAPSHOT).|  
  
## <a name="explanation"></a>Объяснение  
База данных с параметром READ_COMMITTED_SNAPSHOT=ON не поддерживает транзакции, требующие доступа и к таблицам, оптимизированным для памяти, и к дисковым таблицам.  
  
## <a name="user-action"></a>Действие пользователя  
Установите для параметра READ_COMMITTED_SNAPSHOT значение OFF или укажите поддерживаемый уровень изоляции для оптимизированной для памяти таблицы с помощью табличного указания, например WITH (SNAPSHOT). Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

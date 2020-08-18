---
description: MSSQLSERVER_10785
title: MSSQLSERVER_ 10785 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10785 (Database Engine error)
ms.assetid: 32f96c1e-9e94-4603-9bcd-b0c2e4af9fda
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ffe180167a2303d330a0b2541e9e1d3286338b7a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88337380"
---
# <a name="mssqlserver_10785"></a>MSSQLSERVER_10785
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|MSSQLSERVER|  
|Идентификатор события|10785|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P3_HEKATON_XACT|  
|Текст сообщения|*Построение* "*функция*" не поддерживается для активных транзакций, которые обращаются к оптимизированным для памяти таблицам или скомпилированным в собственном коде хранимым процедурам.|  
  
## <a name="user-action"></a>Действие пользователя  
Список неподдерживаемых компонентов и рекомендации по альтернативным решениям см. в статье [Конструкции языка Transact-SQL, не поддерживаемые в In-Memory OLTP](~/relational-databases/in-memory-oltp/transact-sql-constructs-not-supported-by-in-memory-oltp.md).  
  
Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  

---
description: MSSQLSERVER_17083
title: MSSQLSERVER_17083 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17083 (Database Engine error)
ms.assetid: 6c83737d-0531-4fd9-88f6-2da5a150532d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c897b6ee380afc7882b39bca62234d509d29f80f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88332850"
---
# <a name="mssqlserver_17083"></a>MSSQLSERVER_17083
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|Идентификатор события|17083|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|P3_HEKATON_NOT_ATOMIC|  
|Текст сообщения|Телом хранимой процедуры, скомпилированной в собственном коде, должен быть блок ATOMIC.|  
  
## <a name="explanation"></a>Объяснение  
Тело хранимой процедуры, скомпилированной в собственном коде, не содержало блоков ATOMIC.  
  
## <a name="user-action"></a>Действие пользователя  
Скомпилированная в собственном коде хранимая процедура должна содержать блок ATOMIC. Пример:  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE= N'us_english')  
```  
  
Дополнительные сведения см. в разделе [In-Memory OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md).  
  
## <a name="see-also"></a>См. также:  
[Выполняющаяся в памяти OLTP (оптимизация в памяти)](~/relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  

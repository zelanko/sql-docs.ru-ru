---
description: MSSQLSERVER_17803
title: MSSQLSERVER_17803 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17803 (Database Engine error)
ms.assetid: 28591a19-258d-4891-b78a-4686789bb2d7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 848adb2125fdc6ab7427fe076d430b2609d90196
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456413"
---
# <a name="mssqlserver_17803"></a>MSSQLSERVER_17803
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|17803|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_NOMEMORY|  
|Текст сообщения|Во время установления соединения произошла ошибка выделения памяти. Сократите необязательный расход памяти или увеличьте объем системной памяти. Соединение было закрыто.%.*ls|  
  
## <a name="explanation"></a>Объяснение  
Серверу не хватает памяти.  
  
## <a name="user-action"></a>Действие пользователя  
Определите причину нехватки памяти на сервере. Возможно, окажутся полезными общие шаги по устранению неполадок с памятью.  
  

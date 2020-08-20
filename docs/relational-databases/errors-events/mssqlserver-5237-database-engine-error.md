---
description: MSSQLSERVER_5237
title: MSSQLSERVER_5237 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 5237 (Database Engine error)
ms.assetid: 9ff28935-d1eb-47ee-99b3-1a65cb948ce7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5333d2f1cf5da680bff3f4b2dd15b6d52c677166
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88471006"
---
# <a name="mssqlserver_5237"></a>MSSQLSERVER_5237
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|5237|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC4_INDEXED_VIEW_CHECK_QUERY_FAILED_NO_ERRORCODE|  
|Текст сообщения|Перекрестная проверка наборов строк с помощью команды DBCC для объекта NAME (идентификатор объекта O_ID) окончилась неудачей, так как произошла внутренняя ошибка запроса.|  
  
## <a name="explanation"></a>Объяснение  
Внутренняя ошибка привела к тому, что в команде DBCC не удалось выполнить запрос для проверки индексированных представлений.  
  
## <a name="user-action"></a>Действие пользователя  
Повторно выполните команду DBCC.  
  

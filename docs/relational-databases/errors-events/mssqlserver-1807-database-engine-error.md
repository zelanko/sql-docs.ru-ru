---
description: MSSQLSERVER_1807
title: MSSQLSERVER_1807 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1807 (Database Engine error)
ms.assetid: 13c1b240-098b-4d9e-89aa-21599548e074
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5b6b4d42d13539d62f7afc7cc341f2b7b1bee44f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456321"
---
# <a name="mssqlserver_1807"></a>MSSQLSERVER_1807
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|1807|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|CANNOT_EX_LOCK|  
|Текст сообщения|Не удалось получить монопольную блокировку для базы данных «%.*ls». Повторите операцию позже.|  
  
## <a name="explanation"></a>Объяснение  
Операция, которой необходима монопольная блокировка базы данных, не смогла получить ее.  
  
## <a name="user-action"></a>Действие пользователя  
Отключите все соединения с базой данных и повторите запрос.  
  

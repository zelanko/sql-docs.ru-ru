---
description: MSSQLSERVER_9790
title: MSSQLSERVER_9790 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 04ead56d08fb1e2214a99c9ec4dcefb4d816660e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88460840"
---
# <a name="mssqlserver_9790"></a>MSSQLSERVER_9790
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|9790|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|Текст сообщения|Не удалось найти маршрут для входящего сообщения. Системная база данных MSDB, содержащая сведения о маршрутах, находится в режиме SINGLE USER.|  
  
## <a name="explanation"></a>Объяснение  
Произошла ошибка при попытке определения категории сообщения, полученного в автономном режиме, поскольку база данных MSDB находилась в однопользовательском режиме.  
  
## <a name="user-action"></a>Действие пользователя  
С помощью команды ALTER DATABASE измените режим MSDB на MULTI USER.  
  

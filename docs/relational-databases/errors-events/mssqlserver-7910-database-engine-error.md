---
description: MSSQLSERVER_7910
title: MSSQLSERVER_7910 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 7910 (Database Engine error)
ms.assetid: 017a0113-2b17-40b3-a419-30bbc43d46b8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: aac51842ea63515437fe809aff8b1e5c9aeb49ee
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88470836"
---
# <a name="mssqlserver_7910"></a>MSSQLSERVER_7910
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|7910|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC2_REPAIR_PAGE_ALLOCATED|  
|Текст сообщения|Исправление: страница P_ID выделена объекту с идентификатором O_ID, идентификатором индекса I_ID, идентификатором секции PN_ID, идентификатором единицы распределения A_ID (тип TYPE).|  
  
## <a name="explanation"></a>Объяснение  
Это информационное сообщение инструкции REPAIR, указывающее, что страница была размещена в карте распределения индекса (IAM)-страницы.  
  
## <a name="user-action"></a>Действие пользователя  
None  
  

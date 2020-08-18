---
description: MSSQLSERVER_8621
title: MSSQLSERVER_8621 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 8621 (Database Engine error)
ms.assetid: 67f59865-becd-4999-8bb0-90aedd7effbf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5aa58480e63e15b418d3bc2f0ebe38330fe71be3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88331520"
---
# <a name="mssqlserver_8621"></a>MSSQLSERVER_8621
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|8621|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|OPTIMIZER_STACK_OVERFLOW_ERR|  
|Текст сообщения|При оптимизации запроса обработчик запросов исчерпал пространство стека. Упростите запрос.|  
  
## <a name="explanation"></a>Объяснение  
Наиболее вероятной причиной ошибки является размер расширенного запроса. Расширенный запрос получается при подстановке в основной запрос определений каждого из представлений, вычисляемых столбцов, функций [!INCLUDE[tsql](../../includes/tsql-md.md)] и обобщенных табличных выражений, на которые он ссылается, а также каскадных действий, таких как обновление вторичных индексов, представлений и триггеров.  
  
Наиболее вероятно, что размер запроса велик по определенным измерениям, например числу таблиц, на которые ссылаются определения представления, или очень большому скалярному выражению.  
  
## <a name="user-action"></a>Действие пользователя  
Упростите запрос, разбив его на несколько запросов по наибольшему измерению. Первым делом удалите все необязательные элементы запроса, затем попытайтесь добавить временную таблицу и разбить запрос на две части.  Простого выделения части запроса во вложенный запрос, функцию или обобщенное табличное выражение недостаточно, поскольку они будут объединены компилятором [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  

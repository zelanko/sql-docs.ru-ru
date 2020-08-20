---
description: MSSQLSERVER_2508
title: MSSQLSERVER_2508 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9d45680a532698883e5fe8076af79f851ce47ab8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88482852"
---
# <a name="mssqlserver_2508"></a>MSSQLSERVER_2508
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|2508|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|Текст сообщения|Подсчет %.*ls для объекта "%.\*ls", идентификатора индекса %d, идентификатора секции %I64d, идентификатора единицы размещения %I64d (тип %.\*ls) неверен. Запустите команду DBCC UPDATEUSAGE.|  
  
## <a name="explanation"></a>Объяснение  
В версиях [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], предшествующих версии [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], значения количества строк таблиц и индексов, а также количества страниц могут стать неверными. Базы данных, которые были созданы с помощью версий, предшествующих [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], могут содержать неверные подсчеты. Команда DBCC CHECKDB была улучшена, чтобы обнаруживать эти ошибки и возвращать предупреждающие сообщения.  
  
## <a name="user-action"></a>Действие пользователя  
Запустите команду DBCC UPDATEUSAGE для указанного объекта или индекса, или для базы данных, в которой содержится объект, чтобы исправить недопустимые подсчеты.  
  

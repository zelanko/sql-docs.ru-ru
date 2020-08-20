---
description: MSSQLSERVER_17887
title: MSSQLSERVER_17887 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 17887 (Database Engine error)
ms.assetid: ad0806e6-3296-4c32-b103-fccf0f8a8d3d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 02a96dc46232bcce19b89234c07874ed5261ac46
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88456358"
---
# <a name="mssqlserver_17887"></a>MSSQLSERVER_17887
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|17887|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SRV_IO_COMP_LISTENER_NONYIELDING|  
|Текст сообщения|Прослушиватель завершения операций ввода-вывода (0x%lx) исполнитель 0x%p, по-видимому, не возвращает управление узлу %ld. Примерная загрузка ЦП: ядро %I64d мс, пользователь %I64d мс, интервал: %I64d.|  
  
## <a name="explanation"></a>Объяснение  
Указывает на возможную проблему прослушивателя порта завершения операций ввода-вывода на указанном узле при выполнении подпрограммы завершения ввода-вывода для сетевого события чтения или записи. Эта ошибка исчезнет, когда прослушиватель порта завершения операций ввода-вывода на указанном узле вернет управление после выполнения подпрограммы завершения ввода-вывода.  
  
## <a name="user-action"></a>Действие пользователя  
Обратитесь в службу поддержки пользователей Майкрософт.  
  

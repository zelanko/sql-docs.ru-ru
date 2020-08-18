---
description: MSSQLSERVER_15661
title: MSSQLSERVER_15661 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1f851c38ab44e84fa6afd21374c2b2d2680187a4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/17/2020
ms.locfileid: "88333270"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>Сведения  
  
| attribute | Значение |  
| :-------- | :---- |  
|Название продукта|SQL Server|  
|Идентификатор события|15661|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum15661|  
|Текст сообщения|Хранимая процедура sp_estimate_data_compression_savings не может применяться для временных таблиц.|  
  
## <a name="explanation"></a>Объяснение  
В качестве аргумента для хранимой процедуры sp_estimate_data_compression_savings указана временная таблица. Хотя сжатие временных таблиц поддерживается, пользоваться хранимой процедурой sp_estimate_data_compression_savings для оценки сжатия нельзя.  
  
## <a name="user-action"></a>Действие пользователя  
Исключите временную таблицу из числа аргументов хранимой процедуры sp_estimate_data_compression_savings.  
  

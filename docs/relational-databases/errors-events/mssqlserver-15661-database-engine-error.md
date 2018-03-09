---
title: "MSSQLSERVER_15661 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: errors-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: aff56976620f444c707850138185165fe4a82a4e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2017
---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|15661|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|SQLErrorNum15661|  
|Текст сообщения|Хранимая процедура sp_estimate_data_compression_savings не может применяться для временных таблиц.|  
  
## <a name="explanation"></a>Объяснение  
В качестве аргумента для хранимой процедуры sp_estimate_data_compression_savings указана временная таблица. Хотя сжатие временных таблиц поддерживается, пользоваться хранимой процедурой sp_estimate_data_compression_savings для оценки сжатия нельзя.  
  
## <a name="user-action"></a>Действие пользователя  
Исключите временную таблицу из числа аргументов хранимой процедуры sp_estimate_data_compression_savings.  
  

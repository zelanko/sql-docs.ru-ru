---
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
ms.openlocfilehash: 43ea3ea139bfb252e74110b148ac998132c18452
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/01/2020
ms.locfileid: "68100399"
---
# <a name="mssqlserver_15661"></a>MSSQLSERVER_15661
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
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
  

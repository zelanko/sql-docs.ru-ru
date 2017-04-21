---
title: "MSSQLSERVER_15661 | Документация Майкрософт"
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
caps.latest.revision: 11
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 93bd2efde15065f2d7285912a72a10a7ba77d817
ms.lasthandoff: 04/11/2017

---
# <a name="mssqlserver15661"></a>MSSQLSERVER_15661
  
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
  


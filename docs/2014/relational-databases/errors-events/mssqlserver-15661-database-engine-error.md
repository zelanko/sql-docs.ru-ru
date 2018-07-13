---
title: MSSQLSERVER_15661 | Документация Майкрософт
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: supportability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- 15661 (Database Engine error)
ms.assetid: 88b01bfb-74ce-4aa0-aec0-7885261c7ef3
caps.latest.revision: 12
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 6314878bb6a177da1f156545be174346340ec1d6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2018
ms.locfileid: "37413553"
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
  
  

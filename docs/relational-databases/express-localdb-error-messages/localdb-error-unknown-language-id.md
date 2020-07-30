---
title: LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID | Документация Майкрософт
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: performance
ms.topic: reference
ms.assetid: fa082dca-bf88-46e7-b61e-7ac8835a3493
author: stevestein
ms.author: sstein
ms.openlocfilehash: 053fb88279d0aa2ad664e50d4b9c6bbb454f2adb
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245937"
---
# <a name="localdb_error_unknown_language_id"></a>LOCALDB_ERROR_UNKNOWN_LANGUAGE_ID
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
    
## <a name="details"></a>Сведения  
  
| attribute | Значение |
| --------- | ----- |
|Название продукта|SQL Server|  
|Идентификатор события|270|  
|Источник события|Среда выполнения локальной базы данных SQL Server 12.0|  
|Компонент|API среды выполнения локальной базы данных|  
|Текст сообщения|Ошибка при получении локализованного сообщения об ошибке. Язык, указанный параметром «Идентификатор языка», неизвестен.|  
  
## <a name="explanation"></a>Объяснение  
 Запрошенный язык для сообщения об ошибке среды выполнения локальной базы данных неизвестен или не поддерживается.  
  
## <a name="user-action"></a>Действие пользователя  
 Попробуйте запросить один из поддерживаемых языков для сообщений об ошибках среды выполнения локальной базы данных или же язык по умолчанию.  
  
  

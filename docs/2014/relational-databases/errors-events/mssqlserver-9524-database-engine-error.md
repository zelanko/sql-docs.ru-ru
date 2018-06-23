---
title: MSSQLSERVER_9524 | Документация Майкрософт
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
caps.latest.revision: 9
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 8b64e4226d34c1e4541c1bac064e644c69491311
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/19/2018
ms.locfileid: "36191432"
---
# <a name="mssqlserver9524"></a>MSSQLSERVER_9524
    
## <a name="details"></a>Сведения  
  
|||  
|-|-|  
|Название продукта|SQL Server|  
|Идентификатор события|9254|  
|Источник события|MSSQLSERVER|  
|Компонент|SQLEngine|  
|Символическое имя|XMLERR_INVALID_COLUMNSET_XML|  
|Текст сообщения|Переданное XML-содержимое не соответствует установленному формату XML для наборов разреженных столбцов.|  
  
## <a name="explanation"></a>Объяснение  
 Была предпринята попытка изменить набор столбцов. XML-содержимое набора столбцов должно соответствовать ограничениям формата для набора столбцов. Стандартный формат набора столбцов выглядит следующим образом:  
  
 `<column_name_1>value1</column_name_1><column_name_2>value2</column_name_2>...`  
  
 Дополнительные сведения о наборах столбцов см. в разделе «Использование наборов столбцов» электронной документации по [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
## <a name="user-action"></a>Действие пользователя  
 Исправьте формат XML для набора столбцов в инструкции.  
  
  
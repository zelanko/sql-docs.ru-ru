---
title: "MSSQLSERVER_9524 | Документация Майкрософт"
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
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
caps.latest.revision: 10
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 5896357fde2c8930544bd435884701a7a406ee34
ms.contentlocale: ru-ru
ms.lasthandoff: 06/22/2017

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
  


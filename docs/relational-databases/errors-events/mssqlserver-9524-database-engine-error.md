---
title: MSSQLSERVER_9524 | Документация Майкрософт
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9524 (Database Engine error)
ms.assetid: 12da7931-e124-4466-889c-046f1b7b7bfd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 40c707873679d2e5d166f2c1319f971404deabe5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "67903839"
---
# <a name="mssqlserver9524"></a>MSSQLSERVER_9524
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
  

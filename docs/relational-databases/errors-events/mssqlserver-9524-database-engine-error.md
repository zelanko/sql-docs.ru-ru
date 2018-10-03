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
manager: craigg
ms.openlocfilehash: 0fae1116025949657739878f754782d775bf8717
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47653312"
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
  

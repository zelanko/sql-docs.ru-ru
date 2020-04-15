---
title: КОМАНДА SET DELETED (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET DELETED command [ODBC]
ms.assetid: 6b5e0086-156d-471d-8e7f-6c5fa9686cd5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3b3302dc7eecca7135dab9dff5afa376169be0f1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300884"
---
# <a name="set-deleted-command"></a>Команда SET DELETED
Определяется, обрабатываются ли записи, отмеченные для удаления, и доступны ли они для использования в других командах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера; по умолчанию для Visual FoxPro является OFF.) Упоняет, что команды, работающие на записях (включая записи в смежных таблицах), с помощью области игнорируют записи, отмеченные для удаления.  
  
 OFF  
 Упцирует, что записи, отмеченные для удаления, могут быть доступны командами, которые работают на записях (включая записи в смежных таблицах) с помощью области.  
  
## <a name="remarks"></a>Remarks  
 Запросы, которые используют DELETED () для проверки состояния записей могут быть оптимизированы с помощью технологии Visual FoxPro Rushmore, если таблица проиндексирована на DELETED ().  
  
> [!IMPORTANT]  
>  SET DELETED игнорируется, если область действия по умолчанию для команды является текущей записью или если вы включаете область одной записи. ИНДЕКС всегда игнорирует SET DELETED и индексирует все записи в таблице.  
  
## <a name="see-also"></a>См. также:  
 [DELETE (команда SQL)](../../odbc/microsoft/delete-sql-command.md)

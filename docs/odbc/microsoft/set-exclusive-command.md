---
title: Команда SET EXCLUSIVE Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET EXCLUSIVE command [ODBC]
ms.assetid: d4fe12c5-7e8b-4d20-9ea4-2bcaffb271f2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d140c4be3ab850547ac82f9b954e7313b008dbf0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300864"
---
# <a name="set-exclusive-command"></a>Команда SET EXCLUSIVE
Уточняется, открыты ли файлы таблицы для эксклюзивного или совместного использования в сети.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Ограничивает доступность таблицы, открытой в сети для открывшего ее пользователя. Таблица недоступна для других пользователей сети. SET EXCLUSIVE ON также предотвращает доступ ко всем другим пользователям только для чтения.  
  
 OFF  
 (По умолчанию для драйвера; по умолчанию для Visual FoxPro являются ON для глобальной сессии данных и OFF для личной сессии данных.) Позволяет совместному и измененному столиком в сети и измененным любым пользователем сети.  
  
## <a name="remarks"></a>Remarks  
 Изменение настройки SET EXCLUSIVE не меняет статуса ранее открытых таблиц. Например, если таблица открыта с набором SET EXCLUSIVE в ON, а SET EXCLUSIVE позже будет изменена на OFF, таблица сохраняет свой статус исключительного использования.  
  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно настройки ODBC для Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)

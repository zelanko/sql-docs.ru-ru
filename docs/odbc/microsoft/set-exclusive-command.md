---
title: Задание МОНОПОЛЬной команды | Документация Майкрософт
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300864"
---
# <a name="set-exclusive-command"></a>Команда SET EXCLUSIVE
Указывает, следует ли открывать файлы таблиц для монопольного или общего использования в сети.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Ограничивает доступность таблицы, открытой в сети, пользователю, открывшему ее. Таблица недоступна другим пользователям в сети. SET EXCLUSIVE ON также запрещает другим пользователям доступ только для чтения.  
  
 OFF  
 (Значение по умолчанию для драйвера; значения по умолчанию для Visual FoxPro включены для сеанса глобальных данных и ОТКЛЮЧЕНы для сеанса закрытых данных.) Разрешает совместное открытие и изменение таблицы, открытой в сети любым пользователем в сети.  
  
## <a name="remarks"></a>Remarks  
 Изменение параметра SET EXCLUSIVE не приводит к изменению состояния ранее открытых таблиц. Например, если таблица открыта с параметром SET EXCLUSIVE, установленным в ON, а SET EXCLUSIVE в дальнейшем изменяется на OFF, то в таблице сохраняется состояние монопольного использования.  
  
## <a name="see-also"></a>См. также:  
 [Диалоговое окно настройки ODBC для Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)

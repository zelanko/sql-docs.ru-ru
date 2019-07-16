---
title: Команда SET EXCLUSIVE | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9d1a37043d332b54d0d5c5ebb7b2ba9f3acce000
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071762"
---
# <a name="set-exclusive-command"></a>Команда SET EXCLUSIVE
Указывает, открывается ли таблица файлов для монопольного или общего использования в сети.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET EXCLUSIVE ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 Специальные возможности ограничения таблицы, открытый в сети для пользователя, открывшего ее. Таблица не доступны другим пользователям в сети. SET EXCLUSIVE ON также запрещает другим пользователям доступ только для чтения.  
  
 OFF  
 (По умолчанию для драйвера, значения по умолчанию для Visual FoxPro для глобальных данных сеанса и OFF для сеанса личных данных имеют значение ON.) Позволяет открыть в сети для совместного использования и изменения любой пользователь в сети таблицу.  
  
## <a name="remarks"></a>Примечания  
 Изменение параметра ЗАДАЙТЕ МОНОПОЛЬНЫЙ не влияет на состояние ранее открытые таблицы. Например если таблица открывается с УСТАНОВИТЬ МОНОПОЛЬНУЮ присвоено значение ON и УСТАНОВИТЬ МОНОПОЛЬНУЮ позже меняется на OFF, таблице сохраняет его статус эксклюзивного использования.  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно настройки ODBC для Visual FoxPro](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)

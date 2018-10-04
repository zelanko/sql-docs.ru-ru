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
manager: craigg
ms.openlocfilehash: fccbc9b258cbff1e14ccc76e10af9d26efc4b70b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47618822"
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

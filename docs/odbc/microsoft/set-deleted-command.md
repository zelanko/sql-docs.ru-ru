---
title: Команда SET DELETED | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5efbd7e98b430128e52634f5c7d71597afc89ace
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127824"
---
# <a name="set-deleted-command"></a>Команда SET DELETED
Указывает, обрабатываются ли помеченные на удаление записи и ли они становятся доступны для использования в других командах.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET DELETED ON | OFF  
```  
  
## <a name="arguments"></a>Аргументы  
 ON  
 (По умолчанию для драйвера по умолчанию для Visual FoxPro имеет значение OFF.) Указывает, что команды, которые работают с записей (включая записи в связанных таблицах), используя область игнорировать помеченные на удаление записи.  
  
 OFF  
 Указывает, что записи помечаются для удаления осуществляется с помощью команд, которые оперируют записей (включая записи в связанных таблицах), используя область.  
  
## <a name="remarks"></a>Примечания  
 Запрашивает, что использование DELETED (), чтобы проверить состояние записей можно оптимизировать с помощью технологии Visual FoxPro технологию Rushmore, если индексации таблицы на DELETED ().  
  
> [!IMPORTANT]  
>  SET DELETED игнорируется, если область по умолчанию для команды является текущей записи, или если включить в области одной записи. Индекс всегда игнорирует SET DELETED и индексирует все записи в таблице.  
  
## <a name="see-also"></a>См. также  
 [DELETE (команда SQL)](../../odbc/microsoft/delete-sql-command.md)

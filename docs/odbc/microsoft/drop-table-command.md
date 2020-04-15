---
title: Дроп ПЛЕЙТ Команда (ru) Документы Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 779c519f720027aea3a6f6cf2587d3c6e0b59b52
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303425"
---
# <a name="drop-table-command"></a>Команда DROP TABLE
Удаляет таблицу из базы данных, указанную с источником данных, и удаляет ее с диска.  
  
 Visual FoxPro ODBC Driver поддерживает родной визуальный синтаксис языка FoxPro для этой команды. Для получения информации о конкретной для водителей см.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Параметры  
 *Tablename*  
 Определяет таблицу для удаления из базы данных, указанной с источником данных, и удаления с диска.  
  
 *Имени файла*  
 Уотек свободного стола для удаления с диска.  
  
 ?  
 Отображает диалог Удалить, из которого можно выбрать таблицу для удаления из базы данных, указанной с источником данных, и удалить с диска.  
  
## <a name="remarks"></a>Remarks  
 При эне DROP TABLE все первичные индексы, значения по умолчанию и правила проверки, связанные с таблицей, также удаляются. DROP TABLE также влияет на другие таблицы в базе данных, указанные с источником данных, если в этих таблицах есть правила или отношения, связанные с удалением таблицы. Правила и отношения больше не действуют, когда таблица удаляется из базы данных.  
  
## <a name="driver-remarks"></a>Замечания водителя  
 Когда приложение отправляет заявление ODBC S'L DROP TABLE в источник данных, драйвер Visual FoxPro ODBC преобразует команду в команду Visual FoxProDROP TABLE, используя синтаксис, показанный в следующей таблице.  
  
|Синтаксис ODBC|Источник данных|Визуальный синтаксис FoxPro|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *базовый стол-имя*|База данных (файл.dbc)|REMOVE TABLE *TableName* DELETE|  
||Каталог бесплатных таблиц (файлы.dbf)|ERASE *dbfName*<br /><br /> ERASE *cdxName*<br /><br /> ERASE *fptName*|

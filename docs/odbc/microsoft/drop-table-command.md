---
title: Команда DROP TABLE | Документация Майкрософт
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 278950bac7589b8a6b02d894c8133a699c3bd1ef
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2019
ms.locfileid: "68071798"
---
# <a name="drop-table-command"></a>Команда DROP TABLE
Удаляет таблицу из базы данных, указанной с источником данных и удаляет его с диска.  
  
 Драйвер ODBC для Visual FoxPro поддерживает собственный синтаксис языка Visual FoxPro для этой команды. Сведения см. в разделе "Примечания".  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Настройки  
 *TableName*  
 Указывает таблицу для удаления из базы данных, указанной с источником данных и удалить с диска.  
  
 *FileName*  
 Указывает таблицу бесплатно, чтобы удалить с диска.  
  
 ?  
 Отображает диалоговое окно удаления, в котором можно выбрать таблицу для удаления из базы данных, указанной с источником данных и удалить с диска.  
  
## <a name="remarks"></a>Примечания  
 Во время DROP TABLE, то также удаляются все первичные индексы, значения по умолчанию и правила проверки, связанной с таблицей. DROP TABLE также влияет на другие таблицы в базе данных, указанной с источником данных, если эти таблицы содержат правила или связи, связанной с таблицей удаления. Правила и отношения, больше не допустимы, если таблица будет удалена из базы данных.  
  
## <a name="driver-remarks"></a>Драйвер "Примечания"  
 Когда приложение отправляет инструкцию ODBC SQL DROP TABLE к источнику данных, драйвер ODBC для Visual FoxPro преобразует команды в ТАБЛИЦЕ Visual FoxProDROP команду, используя синтаксис, показанный в следующей таблице.  
  
|Синтаксис ODBC|Источник данных|Синтаксис Visual FoxPro|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *base-table-name*|База данных (файл .dbc)|Удаление таблицы *TableName* удалить|  
||Каталог свободного таблиц (.dbf файлы)|СТЕРЕТЬ *dbfName*<br /><br /> СТЕРЕТЬ *cdxName*<br /><br /> СТЕРЕТЬ *fptName*|

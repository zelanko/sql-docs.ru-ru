---
title: "Команда DROP TABLE | Документы Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 271b4305b15be7d4af1b7a8d45a9ec5d42a1adab
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/20/2017
---
# <a name="drop-table-command"></a>Команда DROP TABLE
Удаляет таблицу из базы данных, указанной с источником данных и удаляет его с диска.  
  
 Драйвер ODBC для Visual FoxPro поддерживает собственный синтаксис языка Visual FoxPro для этой команды. Дополнительные сведения см.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Настройки  
 *Имя_таблицы*  
 Указывает таблицу для удаления из базы данных, указанной с источником данных и удалить с диска.  
  
 *FileName*  
 Указывает свободного таблицу, чтобы удалить с диска.  
  
 ?  
 Отображает диалоговое окно Remove, из которого можно выбрать таблицу для удаления из базы данных, указанной с источником данных и удалить с диска.  
  
## <a name="remarks"></a>Замечания  
 Когда выдается DROP TABLE, также удаляются все первичные индексы, значения по умолчанию и правила проверки, связанные с таблицей. DROP TABLE также влияет на другие таблицы в базе данных, указанной с источником данных, если эти таблицы содержат правила или связей, связанные с таблицей удаления. Правила и отношения стали недействительными при удалении таблицы из базы данных.  
  
## <a name="driver-remarks"></a>Драйвер примечания  
 Когда приложение отправляет инструкции ODBC SQL DROP TABLE с источником данных, драйвер ODBC для Visual FoxPro преобразует команды в команду Visual FoxProDROP таблицы, используя синтаксис, показанный в следующей таблице.  
  
|Синтаксис ODBC|Источник данных|Синтаксис Visual FoxPro|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *base-table-name*|Базы данных (.dbc-файл)|Удаление таблицы *TableName* удалить|  
||Каталог свободных таблиц (расширением DBF-файлы)|СТЕРЕТЬ *dbfName*<br /><br /> СТЕРЕТЬ *cdxName*<br /><br /> СТЕРЕТЬ *fptName*|

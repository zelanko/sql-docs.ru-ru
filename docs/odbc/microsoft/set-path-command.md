---
title: Команда SET PATH | Документы Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f4d831d397df3ec0a5ca914b0bfdd530729823f1
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/03/2018
---
# <a name="set-path-command"></a>ПУТЬ команды SET
Указывает путь для поиска файлов. Дополнительные сведения см.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Аргументы  
 ДЛЯ [ *путь*]  
 Указывает каталог, который требуется Visual FoxPro для поиска. Используйте запятую или точку с запятой для разделения каталогов.  
  
## <a name="remarks"></a>Замечания  
 ЗАДАЙТЕ путь можно указать пути поиска для других программ Visual FoxPro, которые можно вызывать хранимые процедуры. ЗАДАЙТЕ путь не изменит путь источника данных, который вы указали для подключения.  
  
 Выдавать ЗАДАТЬ путь без *путь* для восстановления путь к каталогу по умолчанию или папку.  
  
## <a name="driver-remarks"></a>Драйвер примечания  
 Если ЗАДАТЬ путь в хранимой процедуре, оно будет игнорироваться, следующие функции и команды:  
  
-   Функции каталога, такие как [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) и [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) будет игнорировать новый путь и продолжают ссылаться путем, указанным в источнике данных в [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) или [ SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   Команды, такие как SELECT, INSERT, UPDATE, DELETE и CREATE TABLE будет игнорировать новый путь и продолжают ссылаться путем, указанным в источнике данных в **SQLPrepare** или **SQLExecDirect**.  
  
 Если проблема ЗАДАТЬ путь к хранимой процедуре и не задано впоследствии путь обратно в исходное состояние, другие соединения с базой данных будет использовать новый путь (так как значение пути не входит в область данных сеансы).  
  
 Если вы хотите создать, выберите или обновления таблиц в каталоге, отличном от указанного источника данных, укажите полный путь к файлу с вашей команды.  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно установки Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)

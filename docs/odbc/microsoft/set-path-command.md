---
title: Команда SET PATH | Документация Майкрософт
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SET PATH command [ODBC]
ms.assetid: db488d1e-0963-4f45-8c76-a23b9bde9e9d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f3d810e66249779b2d3706e92ea39f89a0f87cff
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/01/2018
ms.locfileid: "47727552"
---
# <a name="set-path-command"></a>Команда SET PATH
Указывает путь для поиска файлов. Сведения см. в разделе "Примечания".  
  
## <a name="syntax"></a>Синтаксис  
  
```  
  
SET PATH TO [Path]  
```  
  
## <a name="arguments"></a>Аргументы  
 ДЛЯ [ *путь*]  
 Задает каталоги, требуется Visual FoxPro для поиска. Используйте запятые или точки с запятой для разделения каталогов используется.  
  
## <a name="remarks"></a>Примечания  
 SET PATH можно указать пути поиска для других программ Visual FoxPro, которые могут вызываться в хранимых процедурах. SET PATH не изменится на путь к источнику данных, который вы указали для подключения.  
  
 Выдавать ЗАДАЙТЕ путь без *путь* для восстановления пути по умолчанию каталог или папку.  
  
## <a name="driver-remarks"></a>Драйвер "Примечания"  
 Если ЗАДАТЬ путь в хранимой процедуре, то оно будет игнорироваться, следующие функции и команды:  
  
-   Например, функции работы с каталогами [SQLTables](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md) и [SQLColumns](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md) игнорирует новый путь и дальше ссылаться на путь, указанный источник данных в [SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md) или [ SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md).  
  
-   Команды, такие как SELECT, INSERT, UPDATE, DELETE и CREATE TABLE будет игнорировать новый путь и дальше ссылаться на путь, указанный источник данных в **SQLPrepare** или **SQLExecDirect**.  
  
 Если вы выполните SET PATH в хранимой процедуре и не впоследствии путь к обратно в исходное состояние, другие подключения к базе данных будет использовать новый путь (так как SET PATH не ограничена сеансов данных).  
  
 Если вы хотите создать, выберите или обновлении таблиц в каталоге, отличном от указанного в источнике данных, укажите полный путь к файлу с помощью вашей команды.  
  
## <a name="see-also"></a>См. также  
 [Диалоговое окно настройки Visual FoxPro ODBC](../../odbc/microsoft/odbc-visual-foxpro-setup-dialog-box.md)   
 [SQLColumns (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqlcolumns-visual-foxpro-odbc-driver.md)   
 [SQLDriverConnect (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)   
 [SQLTables (драйвер ODBC для Visual FoxPro)](../../odbc/microsoft/sqltables-visual-foxpro-odbc-driver.md)
